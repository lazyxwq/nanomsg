CMAKE_MINIMUM_REQUIRED ( VERSION 2.6 ) #cmake最小版本号
MESSAGE ( STATUS, "cmake version must > 2.6", ${PROJECT_BINARY_DIR} ) #输出提示信息
SET ( ASYNC_SRC_LIST async_demo.c ) #设置源文件列表
#SET ( LIBIKCP_SRC ikcp.c )  #设置自定义变量LIBIKCP_SRC
#ADD_LIBRARY ( ikcp SHARED ${LIBIKCP_SRC} )  #添加生成动态库方法
#ADD_LIBRARY ( ikcp STATIC ${LIBIKCP_SRC} ) #添加生成静态库方法
LINK_DIRECTORIES ( .. )
LINK_LIBRARIES ( nanomsg )
ADD_EXECUTABLE ( async_demo ${ASYNC_SRC_LIST} ) #添加生成执行文件方法

SET ( DEVICE_SRC_LIST device_demo.c )
#LINK_DIRECTORIES ( .. )    //在这个可执行文件的规则中不加库信息也行，因为LINK_LIBRARIES和LINK_DIRECTORIES是全局通用的，那么局部通用的规则关键字是哪个呢？？？？
#LINK_LIBRARIES ( nanomsg )
ADD_EXECUTABLE ( device_demo ${DEVICE_SRC_LIST} )

SET (PTHREAD_SRC_LIST pthread_demo.c )
#LINK_DIRECTORIES ( .. )
#LINK_LIBRARIES ( nanomsg pthread )
LINK_LIBRARIES ( pthread )
ADD_EXECUTABLE ( pthread_demo ${PTHREAD_SRC_LIST} )

SET (PUBSUB_SRC_LIST pubsub_demo.c )
#LINK_DIRECTORIES ( .. )
#LINK_LIBRARIES ( nanomsg )
ADD_EXECUTABLE ( pubsub_demo ${PUBSUB_SRC_LIST} )

SET (RPC_SRC_LIST rpc_demo.c )
#LINK_DIRECTORIES ( .. )
#LINK_LIBRARIES ( nanomsg )
ADD_EXECUTABLE ( rpc_demo.c ${RPC_SRC_LIST} )
