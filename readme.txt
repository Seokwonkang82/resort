reservation 수정 
Reservation.java // onPostUpdate 취소요청 시 pub 수행
ReservationCanceled.java // resortId Long type 통일

resort 수정
PolicyHandler.java 취소요청을 받아서 resort 상태 변경
ReservationCanceled.java // resortId Long type 통일

예약 서비스의 resortStatus를 "CANCELED"(하드코딩, 변경해도됨)로 요청 시 리조트 서비스의 리조트 상태를 Available로 변경함


수행 순서

kafka 서버 기동
$kafka_home/bin/kafka-server-start.sh -daemon $kafka_home/config/server.properties & (Labs의 kafka 서버 start)

resort 서비스
리조트 등록 : http http://localhost:8089/resorts resortName="jeju"
리조트 확인 : http http://localhost:8089/resorts

reservation 서비스
예약 : http http://localhost:8089/reservations resortId=1 resortStatus="Not Available" resortName="jeju"
리조트 확인 : http http://localhost:8089/resorts 
예약 확인 : http http://localhost:8089/reservations


취소 : http put http://localhost:8089/reservations/1 resortId=1 resortStatus="CANCELED" resortName="jeju"
리조트 확인 : http http://localhost:8089/resorts
예약 확인 : http http://localhost:8089/reservations