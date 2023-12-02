# <필독> 방화벽 해제 관련 수정, 삽입시 필수
https://es1015.tistory.com/344
여기 사이트 참고해서 본인이 쓰려는 서버 포트 예)8082 방화벽 해제 해줘야함. 안그러면 get요청 밖에 안되고 post(삽입),put(수정) 요청 아예 못함. 

###초기 환경변수 설정방법
server.js 파일 들어가서 주석확인하고 본인 mysql 환경변수로 바꿔주기
// MySQL 연결 설정
const pool = mysql.createPool({
    host: 'localhost',
    user: 'hansung', //본인 mysql 아이디로 바꿔줘야함
    password: 'hansung', //본인 mysql 비번으로 바꿔줘야함
    database: 'cafedb', //본인 db 이름으로 바꿔줘야함
    waitForConnections: true,
    connectionLimit: 10,
    queueLimit: 0
});
// 데이터베이스 연결 확인
pool.getConnection((err, connection) => {
    if (err) throw err; // 연결에 실패한 경우 예외를 던짐
    console.log('Connected as ID ' + connection.threadId);
    connection.release(); // 연결 해제
###본인 포트번호로 수정하기(보통 초기값 8080임)
    app.listen(8082, function(){ 
        console.log('listening on 8082')
    });
});

###카페 관리 시스템 API 문서
개요: 이 API는 카페 관리 시스템과 관련된 메뉴, 재고, 가맹점 정보 관리를 위한 다양한 엔드포인트를 제공합니다.
기본 URL: http://localhost:8082 (본인 포트로 수정해줄 것)

| 번호 | 기능                          | URL                  | 메소드 | 설명                           |
|------|------------------------------|-----------------------|--------|--------------------------------|
| 1    | 메뉴 데이터 가져오기           | /menu_data            | GET    | 모든 메뉴 항목 검색             |
| 2    | 메뉴 카테고리 데이터 가져오기 | /menu_category_data   | GET    | 모든 메뉴 카테고리 검색       |
| 3    | 메뉴 상태 데이터 가져오기     | /menu_state_data      | GET    | 모든 메뉴 상태 검색           |
| 4    | 레시피 데이터 가져오기         | /recipe_data          | GET    | 모든 레시피 검색               |
| 5    | 재고 명칭 데이터 가져오기     | /stock_name_data      | GET    | 모든 재고 명칭 검색           |
| 6    | 재고 카테고리 데이터 가져오기 | /stock_category_data  | GET    | 모든 재고 카테고리 검색       |
| 7    | 가맹점 재고 데이터 가져오기   | /store_stock_data     | GET    | 모든 가맹점 재고 정보 검색     |
| 8    | 가맹점 재고 데이터 수정하기   | /store_stock_data/:stock_id | PUT | 특정 재고 항목 상세 정보 수정 |
| 9    | 가맹점 데이터 가져오기         | /franchise_store_data | GET    | 모든 가맹점 정보 검색           |
| 10   | 새 가맹점 추가하기            | /franchise_store_data | POST   | 새 가맹점 추가                   |

###수정,삽입 테스트하는 방법(포트번호 수정, 방화벽 설정 먼저 해야함)

수정 : cmd 창에
curl -X PUT http://localhost:본인서버포트번호/store_stock_data/1 -H "Content-Type: application/json" -d "{\"stock_amount\": 120, \"stock_price\": 1500}"
입력

삽입 : cmd창에 
curl -X POST http://localhost:본인서버포트번호/franchise_store_data \ -H "Content-Type: application/json" \ -d "{\"store_id\": 2, \"store_owner\": \"lee\", \"store_adress\": \"busan\", \"store_tell\": \"010-2222-3333\", \"store_status_code\": 0}" 
입력, 줄바꿈 안되게 해야 오류 안남





