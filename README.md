object_detection에서 yolo를 통해 publish된 바운딩박스의 정보를 subscribe하여 라이다의 데이터와 결합하여 사용했습니다. 사전에 MATLAB의 LiDAR-Camera calibrator를 통해 구한 파라미터를 통해 LiDAR를 톨해 인지한 객체의 바운딩박스의 정보를 카메라의 좌표계로 변환합니다. 그래서 LiDAR의 바운딩박스와 yolo에서 publis된 바운딩박스가 정해진 IoU의 임계값만큼 일치하면 두 데이터를 합쳤습니다. LiDAR를 통해 인지한 거리데이터와 yolo를 통해 인지한 class의 정보를 판단에게 넘겨서 경로생성을 할 수 있도록 했습니다.

1. src/amz : 노란 라바콘과 파란 라바콘을 구분하는 amz 미션을 위한 소스코드들이 있습니다.
2. src/deli : 표지판을 구분하는 배달 미션을 위한 소스코드들이 있습니다.
3. src/lidar_pre :  [복셀 그리드 방식의 다운샘플링->ROI(관심영역) 설정->유클리디언 거리를 통한 클러스터링]의 LiDAR 데이터 전처리를 통해 인지한 객체에 3D bounding box를 만드는 소스코드가 있습니다.

그 외에도 개발 혹은 LiDAR-Camera 세팅의 편의를 위한 코드들이 패키지에 포함되어 있습니다.
