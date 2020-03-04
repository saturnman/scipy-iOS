# scipy-iOS
This is scipy iOS port repository, now not all modules work properly.
iOS has many restrictions and library must statically linked. many modules
and functions must be fixed and disabled.

*usage:*
1. python 2.7 and numpy must built for iOS already.
2. go to release page and download static library files and python package sources and put int appropirate position.
3. use the following code template to initialize available modules
4. new you can write python to test the module you want to use to see if it is work properly. 
<pre>
<code>
#import <UIKit/UIKit.h>
#import "AppDelegate.h"
#include "Python.h"
PyMODINIT_FUNC init_fblas(void);
PyMODINIT_FUNC init_flapack(void);
PyMODINIT_FUNC init_iterative(void);
PyMODINIT_FUNC init_arpack(void) ;
PyMODINIT_FUNC init_calc_lwork(void) ;
PyMODINIT_FUNC init_interpolative(void) ;
PyMODINIT_FUNC init_flinalg(void) ;
PyMODINIT_FUNC init_lbfgsb(void) ;
PyMODINIT_FUNC init_cobyla(void) ;
PyMODINIT_FUNC init_nnls(void) ;
PyMODINIT_FUNC init_slsqp(void) ;
PyMODINIT_FUNC init_dop(void) ;
PyMODINIT_FUNC init_test_odeint_banded(void) ;
PyMODINIT_FUNC init_fftpack(void) ;
PyMODINIT_FUNC init__odrpack(void);
PyMODINIT_FUNC init_vq(void); /*proto*/
PyMODINIT_FUNC init_vq(void);
PyMODINIT_FUNC init_hierarchy(void); /*proto*/
PyMODINIT_FUNC init_hierarchy(void);
PyMODINIT_FUNC init_nd_image(void);
PyMODINIT_FUNC init_ni_label(void); /*proto*/
PyMODINIT_FUNC init_ni_label(void);
PyMODINIT_FUNC init_solve_toeplitz(void); /*proto*/
PyMODINIT_FUNC init_solve_toeplitz(void);
PyMODINIT_FUNC init_decomp_update(void); /*proto*/
PyMODINIT_FUNC init_decomp_update(void);
PyMODINIT_FUNC init_minpack(void) ;
PyMODINIT_FUNC init_zeros(void);
PyMODINIT_FUNC init_quadpack(void) ;
PyMODINIT_FUNC init_odepack(void);
PyMODINIT_FUNC init_ufuncs(void); /*proto*/
PyMODINIT_FUNC init_ufuncs(void);
PyMODINIT_FUNC init_ellip_harm_2(void); /*proto*/
PyMODINIT_FUNC init_ellip_harm_2(void);
PyMODINIT_FUNC init_ppoly(void); /*proto*/
PyMODINIT_FUNC init_ppoly(void);
PyMODINIT_FUNC init_fitpack(void) ;
PyMODINIT_FUNC init_superlu(void);
PyMODINIT_FUNC init_csparsetools(void); /*proto*/
PyMODINIT_FUNC init_csparsetools(void);
PyMODINIT_FUNC init_sparsetools(void);
PyMODINIT_FUNC init_min_spanning_tree(void); /*proto*/
PyMODINIT_FUNC init_min_spanning_tree(void);
PyMODINIT_FUNC init_reordering(void); /*proto*/
PyMODINIT_FUNC init_reordering(void);
PyMODINIT_FUNC init_shortest_path(void); /*proto*/
PyMODINIT_FUNC init_shortest_path(void);
PyMODINIT_FUNC init_tools(void); /*proto*/
PyMODINIT_FUNC init_tools(void);
PyMODINIT_FUNC init_traversal(void); /*proto*/
PyMODINIT_FUNC init_traversal(void);
PyMODINIT_FUNC init_distance_wrap(void);
PyMODINIT_FUNC init_spectral(void); /*proto*/
PyMODINIT_FUNC init_spectral(void);
PyMODINIT_FUNC init_max_len_seq(void); /*proto*/
PyMODINIT_FUNC init_max_len_seq(void);
PyMODINIT_FUNC init_rank(void); /*proto*/
PyMODINIT_FUNC init_rank(void);
PyMODINIT_FUNC init_ufuncs_cxx(void); /*proto*/
PyMODINIT_FUNC initspecfun(void);
PyMODINIT_FUNC initcython_blas(void);
PyMODINIT_FUNC initcython_lapack(void); /*proto*/
PyMODINIT_FUNC init_ellip_harm_2(void); /*proto*/
PyMODINIT_FUNC initvode(void);
PyMODINIT_FUNC initlsoda(void);
PyMODINIT_FUNC initdfitpack(void);
PyMODINIT_FUNC initinterpnd(void); /*proto*/
PyMODINIT_FUNC initckdtree(void); /*proto*/
int main(int argc, char * argv[])
    {
    @autoreleasepool {
        NSString * rootPath = [[NSBundle mainBundle] resourcePath];

        Py_SetPythonHome((char *)[rootPath cStringUsingEncoding:NSUTF8StringEncoding]);
        Py_OptimizeFlag = 1; 
        Py_Initialize();

        NSString *documentsDirectory = [paths firstObject];
        NSString *code = [NSString stringWithFormat:@"import site;import os;os.chdir('%@')",documentsDirectory];
        PyRun_SimpleString((char*)[code cStringUsingEncoding:NSUTF8StringEncoding]);
        
        init_sparsetools();
        initvode();
        initlsoda();
        init_dop() ;
        init_odepack();
        init_quadpack();

        init_ufuncs_cxx();
        init_ufuncs();

        init_flinalg() ;


        init_fblas();

        init_rank();
        initspecfun();
        init_fblas();
        init_flapack();
        init_solve_toeplitz();
        initcython_blas();
        initcython_lapack();

        init_decomp_update();
        init_ellip_harm_2();

        //---------
        init_vq();
        init_fftpack();
        init_superlu();


        init_fitpack();
        initdfitpack();
        init_csparsetools();

        init_tools();
        init_traversal();

        init_reordering();

        init_min_spanning_tree();


        init_shortest_path();

        init_spectral();




        int result = UIApplicationMain(argc, argv, nil, NSStringFromClass([AppDelegate class]));
        Py_Finalize();

        return result;
    }
}

</code>
</pre>
