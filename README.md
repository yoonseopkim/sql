# <필독> 방화벽 해제 관련 수정, 삽입시 필수
https://es1015.tistory.com/344
여기 사이트 참고해서 본인이 쓰려는 서버 포트 예)8082 방화벽 해제 해줘야함. 안그러면 get요청 밖에 안되고 post(삽입),put(수정) 요청 아예 못함. 



카페 관리 시스템 API 문서
개요
이 API는 카페 관리 시스템과 관련된 메뉴, 재고, 가맹점 정보 관리를 위한 다양한 엔드포인트를 제공합니다.

기본 URL
http://localhost:8082 (본인 포트로 수정해줄 것)

엔드포인트
1. 메뉴 데이터 가져오기
   URL: /menu_data
   메소드: GET
   설명: 모든 메뉴 항목을 검색합니다.
   응답: 메뉴 항목의 JSON 배열.
2. 메뉴 카테고리 데이터 가져오기
   URL: /menu_category_data
   메소드: GET
   설명: 모든 메뉴 카테고리를 검색합니다.
   응답: 메뉴 카테고리의 JSON 배열.
3. 메뉴 상태 데이터 가져오기
   URL: /menu_state_data
   메소드: GET
   설명: 모든 메뉴 상태를 검색합니다.
   응답: 메뉴 상태의 JSON 배열.
4. 레시피 데이터 가져오기
   URL: /recipe_data
   메소드: GET
   설명: 모든 레시피를 검색합니다.
   응답: 레시피의 JSON 배열.
5. 재고 명칭 데이터 가져오기
   URL: /stock_name_data
   메소드: GET
   설명: 모든 재고 명칭을 검색합니다.
   응답: 재고 명칭의 JSON 배열.
6. 재고 카테고리 데이터 가져오기
   URL: /stock_category_data
   메소드: GET
   설명: 모든 재고 카테고리를 검색합니다.
   응답: 재고 카테고리의 JSON 배열.
7. 가맹점 재고 데이터 가져오기
   URL: /store_stock_data
   메소드: GET
   설명: 모든 가맹점 재고 정보를 검색합니다.
   응답: 가맹점 재고의 JSON 배열.
8. 가맹점 재고 데이터 수정하기
   URL: /store_stock_data/:stock_id
   메소드: PUT
   설명: 특정 재고 항목의 상세 정보를 업데이트합니다.
   요청 파라미터:
   stock_id (URL 파라미터): 수정할 재고의 ID.
   stock_amount, stock_price, stock_import_date, stock_expiration_date (JSON 본문)
   응답: 성공적인 업데이트 시의 메시지.
9. 가맹점 데이터 가져오기
   URL: /franchise_store_data
   메소드: GET
   설명: 모든 가맹점 정보를 검색합니다.
   응답: 가맹점 정보의 JSON 배열.
10. 새 가맹점 추가하기
    URL: /franchise_store_data
    메소드: POST
    설명: 새 가맹점을 추가합니다.
    요청 본문:
    store_id, store_owner, store_adress, store_tell, store_status_code (JSON 본문)
    응답: 성공적인 추가 시의 메시지.



