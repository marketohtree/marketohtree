<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>'놀러와요 시장, 놀장' 입점신청서</title>
    <style>
        body {
            font-family: Roboto, Inter, Noto Sans;
            line-height: 1.6;
        }
        header, footer {
            color:aliceblue;
            background-color: #ff820e;
            padding: 5px 5px;
            text-align: center;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
            width: 55%; /* 배경 박스의 너비 줄이기 */
            margin: 0 auto; /* 가운데 정렬 */
            border-radius: 10px; /* 박스 모서리 둥글게 (선택사항) */
        }
        .container {
            margin: 20px auto;
            max-width: 900px;
        }
        .section {
            margin-bottom: 20px;
        }
        h1 {
            font-size: 50px; /* 픽셀 단위 */
        }
        h2 {
            border-bottom: 2px solid #333;
            padding-bottom: 5px;
            font-weight: 700;
            letter-spacing: 2px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
    color: #333;
        }
        label {
            display: block;
            margin: 10px 0 5px;
        }
        input, textarea, select, button {
            width: 100%;
            padding: 10px;
            margin-bottom: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
        }
        button {
            background-color: #2ced63;
            color: white;
            cursor: pointer;
        }
        button:hover {
            background-color: #ffaf46;
        }
        .hidden {
            display: none;
        }
        }
    </style>
    <style>
        li {
            margin-bottom: 10px; /* 각 항목 아래에 10px 간격 추가 */
        }
    </style>
<script>
    function toggleCustomInput(event, customInputId) {
        const selectedValue = event.target.value;
        const customInput = document.getElementById(customInputId);

        if (selectedValue === "기타") {
            customInput.classList.remove("hidden");
        } else {
            customInput.classList.add("hidden");
            customInput.querySelector("input").value = ""; // 입력 내용 초기화
        }
    }
    </script>
    <script>
        function validateFileSize(event) {
            const files = event.target.files; // 업로드된 파일들
            const maxFileSize = 10 * 1024 * 1024; // 10MB (바이트로 계산)

            for (let i = 0; i < files.length; i++) {
                if (files[i].size > maxFileSize) {
                    alert(`파일 ${files[i].name}의 크기가 10MB를 초과합니다.`);
                    event.target.value = ""; // 입력 초기화
                    return;
                }
            }
        }
    </script>
    <script>
        // 1번 버튼: 개인정보 동의 정보 저장
        function saveAgreement() {
            fetch('/save-agreement', { // 서버로 요청
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ agreement: true })
            })
            .then(response => response.json())
            .then(data => alert('동의가 저장되었습니다.'))
            .catch(error => console.error('Error:', error));
        }

        // 2번 버튼: 신청서 PDF 생성 및 이메일 전송
        function submitApplication() {
            // 필요한 데이터 수집
            const formData = new FormData(document.querySelector('form'));
            
            fetch('/submit-application', { // 서버로 요청
                method: 'POST',
                body: formData
            })
            .then(response => response.json())
            .then(data => alert('신청서가 제출되었습니다.'))
            .catch(error => console.error('Error:', error));
        }

        // 3번 버튼: 이메일 보내기 및 전화 연결
        function contactSupport() {
            if (confirm('전화 연결하시겠습니까?')) {
                window.location.href = 'tel:01095939264';
            } else {
                window.location.href = 'mailto:shoh@market-tree.com';
            }
        }
    </script>


<script>
    async function uploadToS3(event) {
        event.preventDefault();
        
        const form = document.getElementById('entry-form');
        const formData = new FormData(form);

        // 데이터를 JSON으로 변환
        const data = {};
        formData.forEach((value, key) => {
            data[key] = value;
        });

        const s3Url = 'https://your-api-gateway-endpoint.amazonaws.com/prod/upload'; // API Gateway 엔드포인트

        // 데이터를 S3로 업로드
        try {
            const response = await fetch(s3Url, {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify(data),
            });

            if (response.ok) {
                alert('신청서가 성공적으로 제출되었습니다!');
            } else {
                alert('신청서 제출에 실패했습니다.');
            }
        } catch (error) {
            console.error('Error uploading to S3:', error);
        }
    }
</script>
</head>
<body>

<header>
    <h1>'놀러와요 시장, 놀장' 입점신청서</h1>
</header>

<div class="container">
    <!-- 입점/제휴문의 -->
    <div class="section" id="inquiry">
        <h2>'놀장' 운영사 : 주식회사 마켓트리<br>
            <a href="https://market-tree.com" target="_blank" style="color: #ff18f0; text-decoration: none;">https://www.market-tree.com</a><br>
            <a href="https://mall.noljang.co.kr" target="_blank" style="color: #ff18f0; text-decoration: none;">https://mall.noljang.co.kr</a><br>
            대표자 : 이광명<br>
            사업자등록번호 : 836-86-00441<br>
            사업장소재지 : 서울특별시 강남구 테헤란로25길23, 3층(역삼동, 태광빌딩)<br>
            <br>
            <div style="position: relative; margin-bottom: 20px;">
                <!-- 왼쪽 텍스트 -->
                <div style="padding-right: 200px;"> <!-- 오른쪽에 고정된 여백 -->
                    <p>
                        FAX<br>
                        02-6953-6239<br>
                        TEL<br>
                        02-2039-6240<br>
                        EMAIL<br>
                        noljang@market-tree.com<br>
                    </p>
                </div>
                <!-- 오른쪽 이미지 -->
                <div style="position: absolute; top: 0; right: 0; height: 100%; width: 500px;">
                    <img src="https://imgur.com/a/wsABRkO" 
                         alt="활기찬 전통시장 이미지" 
                         style="height: 100%; width: 100%; object-fit: cover; border-radius: 5px; border: 1px solid #ddd;">
                </div>
            </div>            
        <form>
            <label for="inquiry-type">입점가능여부 확인</label>
            <select id="inquiry-type" name="inquiry-type">
                <option value="입점가능여부 확인" disabled selected>전통시장/비전통시장 여부를 선택하세요</option>
                <option value="전통시장 소속">전통시장 상인회 소속 상점</option>
                <option value="전통시장 구역내 비소속">전통시장 구역내 유통업체</option>
                <option value="비전통시장">비전통시장 유통업체</option>
            </select>
            <div class="container">
                <form id="entry-form" onsubmit="handleSubmit(event)">
                    <label for="business-registration">사업자등록증 업로드</label>
                    <input type="file" id="business-registration" name="business-registration" onchange="validateFileSize(event)" required>
        
                    <label for="bank-copy">통장사본 업로드</label>
                    <input type="file" id="bank-copy" name="bank-copy" onchange="validateFileSize(event)" required>
        
                    <label for="sales-proof">매출액 증빙자료 업로드</label>
                    <input type="file" id="sales-proof" name="sales-proof" onchange="validateFileSize(event)" required>
        
                    <label for="ecommerce-license">통신판매업 신고증 업로드</label>
                    <input type="file" id="ecommerce-license" name="ecommerce-license" onchange="validateFileSize(event)" required>
        
                    <button type="submit">입점 신청</button>
                </form>
            </div>
            
            <label for="name">사업자명</label>
            <input placeholder="사업자등록증상 사업자명" type="text" id="biz_info" name="biz_name">
            
            <label for="phone">'놀장'에서 사용 원하시는 상점명</label>
            <input placeholder="놀장 플랫폼에서 쓰고싶은 상점명"type="text" id="biz_info" name="noljang_name">
            
            <label for="email">사업자번호</label>
            <input placeholder="사업자등록증상 사업자번호"type="number" id="biz_info" name="biz_#">
            
            <label for="subject">사업장 주소</label>
            <input placeholder="도로명주소로 적어주셔요" type="text" id="biz_info" name="biz_address">
            
            <label for="file">대표자 연락처</label>
            <input placeholder="핸드폰 번호 적어주셔요" type="number" id="biz_info" name="owner_#">

            <!-- 업태/업종 -->
            <label for="business-type">업태/업종</label>
            <select id="business-type" name="business-type" onchange="toggleCustomInput(event, 'custom-business-type')">
                <option value="" disabled selected>농산/축산/수산/가공식품 등 중 선택하세요</option>
                <option value="농산">농산</option>
                <option value="축산">축산</option>
                <option value="수산">수산</option>
                <option value="공산품">가공식품</option>
                <option value="기타">기타</option>
            </select>
            <label for="name">종업원수</label>
            <input placeholder="숫자만 적어주셔요" type="number" id="biz_info" name="biz_staffs">
            <label for="name">매출액(백만원)_전년도</label>
            <input placeholder="백만원 단위만 숫자로 적어주셔요" type="number" id="biz_info" name="biz_size">
            <!-- 기타 선택 시 표시 -->
            <div id="custom-business-type" class="hidden">
                <label for="custom-business">직접 입력</label>
                <input type="text" id="custom-business" name="custom-business" placeholder="기타 업태/업종을 입력하세요">
            </div>

            <label for="message">'놀장'에 바라는 점_자유기재</label>
            <textarea id="message" name="message" rows="5"></textarea>
            
            <label>

            <button type="submit">개인정보 수집 및 이용에 동의합니다.</button>
            </label>
            
            <button type="submit">제출</button>

        </form>
    </div>

    <!-- 입점제휴안내 -->
    <div class="section" id="guidelines">
        <h2>입점제휴안내</h2>
        <p><strong>담당자 안내:</strong></p>
        <ul>
            <li>전통시장 제휴 및 사업연계 관련문의: 오송현 팀장 (Tel: 010-9593-9264, Email: shoh@market-tree.com)</li>
            <li>상품 운영/개발 담당: 김용대 본부장 (02-2039-6240, ydkim@market-tree.com)</li>
        </ul>
        <p><strong>입점절차:</strong></p>
        <ol>
            <li>STEP 01: 입점신청서 작성 후 제출<br>
                -입점심사 통과 후 입점계약서 작성 필요합니다.
            </li>
            <li>STEP 02: 담당자 확인 개별연락<br>
                -최대 10일 이내 추가정보 확인목적으로 연락드리겠습니다.<br>
            </li>
            <li>STEP 03: 입점심사 후 입점여부 결정<br>
                -기본자격 심사 후 과거이력 및 평판조회 후 입점이 결정됩니다.<br>
            </li>
            <li>STEP 04: 입점계약서 작성/체결<br>
                -입점결정 후 보내드리는 계약서 양식에 따라 자필기재 및 온라인 발송&입점 가맹비 최초 1회 30만원 납부 후 계약체결<br>
            </li>
            <li>STEP 05: 입점교육 수료 후 상품등록<br>
                -소정의 온라인 교육 및 시험<br>
            </li>
            <li>STEP 06: 상품판매 및 정산<br>
                -정산기간 :<br>
                &nbsp;매월 1~15일 주문승인건->매월 말일 정산지급, 매월 16~말일 주문승인건->익월 15일 정산지급<br> 
                &nbsp;※휴일끼는 경우, 휴일 다음날 지급※<br>
            </li>
        </ol>
        <p><strong>입점자격:</strong> 온누리상품권 가맹점, 택배발송 가능한 공급사, 온라인 주문확인 가능, 정식 사업자등록 (간이사업자 제외)</p>
        <p><strong>입점불가상품:</strong> 주류, 담배, 의약품, 파손 우려 상품, 소비자 문제 야기 식품</p>
    </div>

    <!-- 대량구매상담 -->
    <div class="section" id="bulk-purchase">
        <h2>상품대량등록 상담</h2>
        <p>문의: 오송현 팀장 (Tel: 010-9593-9264, Email: shoh@market-tree.com)</p>
        <p>이미 입점신청/계약되었으나, 상품대량등록 필요하신 경우 연락부탁드려요.</p>
        <a href="http://mall.noljang.co.kr" target="_blank">
            <button>상담 신청</button>
        </a>
    </div>
</div>

<footer>
    <p>(주)마켓트리 대표이사 : 이광명<br> 
        사업자등록번호 : 836-86-00441<br>
        주소 : 서울특별시 강남구 테헤란로 25길 23 3층<br>
        © 2023 market Tree INC. ALL RIGHTS RESERVED</p>
</footer>

</body>
</html>
