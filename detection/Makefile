#export LD_LIBRARY_PATH=/home/thomas/opencv/build-3.2.0/x86_64/debug/lib
OPENCV_BRANCH:=3.2.0
OPENCV_SRC :=/home/thomas/opencv/${OPENCV_BRANCH}
OPENCV_OUT:=/home/thomas/opencv/build-${OPENCV_BRANCH}/x86_64/debug

CC = g++
#OPENCV = -L${OPENCV_OUT}/lib/ -L/local/lib/ -lopencv_highgui -lopencv_core -lopencv_imgproc -I/local/include/opencv

OPENCVLIBS= -L${OPENCV_OUT}/lib/ -lopencv_highgui -lopencv_core \
			-lopencv_imgproc  \
			-lopencv_flann \
			-lopencv_calib3d -lopencv_ml \
			-lopencv_video  -lopencv_videoio \
			-lopencv_objdetect -lopencv_photo \
			-lopencv_imgcodecs \
			-lopencv_features2d

#			-lopencv_contrib -lopencv_legacy
#			-lopencv_gpu
#			-lopencv_ocl -lopencv_nonfree \

INC := \
	-I. \
	-I${OPENCV_SRC}/include \
	-I${OPENCV_SRC}/include/opencv \
	-I${OPENCV_SRC}/modules/core/include \
	-I${OPENCV_SRC}/modules/calib3d/include \
	-I${OPENCV_SRC}/modules/features2d/include \
	-I${OPENCV_SRC}/modules/flann/include \
	-I${OPENCV_SRC}/modules/highgui/include \
	-I${OPENCV_SRC}/modules/imgcodecs/include \
	-I${OPENCV_SRC}/modules/video/include \
	-I${OPENCV_SRC}/modules/videoio/include \
	-I${OPENCV_SRC}/modules/imgproc/include \
	-I${OPENCV_SRC}/modules/ml/include \
	-I${OPENCV_SRC}/modules/objdetect/include \
	-I${OPENCV_SRC}/modules/photo/include \
	-I${OPENCV_SRC}/modules/shape/include \
	-I${OPENCV_SRC}/modules/stitching/include \
	-I${OPENCV_SRC}/modules/superres/include \
	-I${OPENCV_SRC}/modules/videostab/include \
	-I${OPENCV_OUT} \
	-I/usr/local/include/ \

CFLAGS += $(INC) -DDEBUG  -pg -g3
CXXFLAGS += $(INC)  -DDEBUG  -pg -g3

all : demo
demo: common.cpp common.hpp TrainDetector.cpp TrainDetector.hpp LearnGAB.cpp LearnGAB.hpp
	$(CC) demo.cpp common.cpp TrainDetector.cpp LearnGAB.cpp $(CFLAGS) $(OPENCVLIBS) -fopenmp -o demo -O3 -DNDEBUG
