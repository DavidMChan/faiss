# specify header and cpp files
file(GLOB_RECURSE faiss_gpu_headers ${CMAKE_CURRENT_SOURCE_DIR}/*.h)
file(GLOB_RECURSE faiss_gpu_cpp ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp)
file(GLOB_RECURSE faiss_gpu_cuh ${CMAKE_CURRENT_SOURCE_DIR}/*.cuh)
file(GLOB_RECURSE faiss_gpu_cu ${CMAKE_CURRENT_SOURCE_DIR}/*.cu)

include_directories(SYSTEM ${CUDA_INCLUDE_DIRS})
list(APPEND CUDA_LINKER_LIBS ${CUDA_CUDART_LIBRARY} ${CUDA_curand_LIBRARY} ${CUDA_CUBLAS_LIBRARIES})

cuda_add_library(gpufaiss SHARED ${faiss_gpu_headers} ${faiss_gpu_cpp} ${faiss_gpu_cuh} ${faiss_gpu_cu})
