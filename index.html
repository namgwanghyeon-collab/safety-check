// DOM 요소(HTML 태그)를 미리 찾아 변수에 저장
const tableBody = document.getElementById('equipmentTableBody');
const addRowBtn = document.getElementById('addRowBtn');
const editModal = document.getElementById('editModal');
const closeModalBtn = document.getElementById('closeModalBtn');
const saveChangesBtn = document.getElementById('saveChangesBtn');
const editForm = document.getElementById('editForm');

let currentRow = null; // 현재 편집 중인 행(TR)을 저장할 변수

// --- 1. 'No' 열 번호 자동 갱신 함수 ---
function updateRowNumbers() {
    // querySelectorAll은 NodeList를 반환하므로 forEach 사용
    const rows = tableBody.querySelectorAll('tr.data-row');
    rows.forEach((row, index) => {
        // 첫 번째 <td> (No 열)을 찾아서 텍스트를 업데이트
        const cell = row.querySelector('.row-number-cell');
        if (cell) {
            cell.innerText = index + 1;
        }
    });
}

// --- 2. '검교정 상태'에 따라 색상 Span을 생성하는 함수 ---
function getStatusSpan(statusText) {
    let bgColor, textColor;
    switch (statusText.trim()) {
        case '정상':
            bgColor = 'bg-green-100';
            textColor = 'text-green-800';
            break;
        case '교정 필요':
            bgColor = 'bg-yellow-100';
            textColor = 'text-yellow-800';
            break;
        case '기한 만료':
            bgColor = 'bg-red-100';
            textColor = 'text-red-800';
            break;
        default: // 'N/A' 또는 그 외
            bgColor = 'bg-gray-100';
            textColor = 'text-gray-800';
            break;
    }
    // Tailwind 클래스가 적용된 HTML 문자열 반환
    return `<span class="px-3 py-1 inline-flex text-xs leading-5 font-semibold rounded-full ${bgColor} ${textColor}">
                ${statusText}
            </span>`;
}

// --- 3. 테이블 정렬 기능 ---
document.querySelectorAll('th.sortable-header').forEach(header => {
    header.addEventListener('click', function() {
        const tbody = tableBody;
        const column = this.cellIndex; // 클릭한 헤더의 열 인덱스
        // data-sort 속성을 읽어 정렬 방향 확인
        let currentDirection = this.getAttribute('data-sort');
        const isAscending = currentDirection === 'asc';
        const newDirection = isAscending ? 'desc' : 'asc';
        
        // 1. 모든 헤더의 정렬 방향과 화살표 초기화
        document.querySelectorAll('th.sortable-header').forEach(h => {
            h.setAttribute('data-sort', '');
            h.querySelector('.sort-indicator').innerText = '';
        });

        // 2. 현재 클릭한 헤더에만 정렬 방향과 화살표 설정
        this.setAttribute('data-sort', newDirection);
        // newDirection이 'asc' (오름차순) 일 때 '▲' 표시, 'desc' (내림차순) 일 때 '▼' 표시
        this.querySelector('.sort-indicator').innerText = newDirection === 'asc' ? '▲' : '▼';

        // 3. 행(TR)들을 배열로 변환하여 정렬
        const rows = Array.from(tbody.querySelectorAll('tr.data-row'));
        rows.sort((a, b) => {
            // 각 행의 해당 열(TD)에 있는 텍스트를 가져옴
            const aText = a.cells[column].innerText;
            const bText = b.cells[column].innerText;
            
            // 정렬 로직: newDirection이 'asc'이면 오름차순, 'desc'이면 내림차순
            if (newDirection === 'asc') {
                return aText.localeCompare(bText, 'ko'); // 한국어 기준으로 정렬
            } else {
                return bText.localeCompare(aText, 'ko');
            }
        });

        // 4. 정렬된 행을 다시 tbody에 순서대로 추가
        rows.forEach(row => tbody.appendChild(row));

        // 5. 정렬 후 'No' 열 갱신
        updateRowNumbers();
    });
});

// --- 4. 편집 모달 팝업창 관련 ---

// 모달 열기 함수
function openModal(row) {
    currentRow = row; // 현재 행 저장
    const cells = row.getElementsByTagName('td');
    
    // 폼에 현재 데이터 채우기 (No.는 0번째, 장비명은 1번째...)
    document.getElementById('editName').value = cells[1].innerText;
    document.getElementById('editNumber').value = cells[2].innerText;
    document.getElementById('editAsset').value = cells[3].innerText;
    // '검교정 상태'는 span 태그 안의 텍스트를 가져와야 함
    const statusSpan = cells[4].querySelector('span');
    document.getElementById('editStatus').value = statusSpan ? statusSpan.innerText : cells[4].innerText;
    document.getElementById('editLastDate').value = cells[5].innerText;
    document.getElementById('editNextDate').value = cells[6].innerText;
    document.getElementById('editManager').value = cells[7].innerText;

    editModal.classList.remove('hidden'); // 모달 보이기
}

// 모달 닫기 함수
function closeModal() {
    editModal.classList.add('hidden'); // 모달 숨기기
    currentRow = null; // 현재 행 선택 해제
}

// '신규 장비 추가' 버튼 클릭 이벤트
if (addRowBtn) {
    addRowBtn.addEventListener('click', function() {
        const newRowHTML = `
            <tr class="data-row">
                <td class="row-number-cell px-6 py-4 text-sm text-gray-500"></td>
                <td class="px-6 py-4 text-sm font-medium text-gray-900">(장비명 입력)</td>
                <td class="px-6 py-4 text-sm text-gray-700">(장비번호 입력)</td>
                <td class="px-6 py-4 text-sm text-gray-700">(자산번호 입력)</td>
                <td class="px-6 py-4 text-sm text-gray-700">
                    ${getStatusSpan('N/A')}
                </td>
                <td class="px-6 py-4 text-sm text-gray-700">2025-01-01</td>
                <td class="px-6 py-4 text-sm text-gray-700">2026-01-01</td>
                <td class="px-6 py-4 text-sm text-gray-700">(담당자 입력)</td>
                <td class="px-6 py-4 text-center text-sm">
                    <button class="delete-btn text-red-500 hover:text-red-700 transition duration-150 ease-in-out">삭제</button>
                </td>
            </tr>
        `;
        // 'beforeend'는 tableBody의 마지막 자식 뒤에 HTML을 삽입
        tableBody.insertAdjacentHTML('beforeend', newRowHTML);

        // 행 추가 후 'No' 열 갱신
        updateRowNumbers();
    });
}

// 테이블 영역 클릭 이벤트 (이벤트 위임)
if (tableBody) {
    tableBody.addEventListener('click', function(e) {
        // '삭제' 버튼을 클릭한 경우
        const deleteButton = e.target.closest('.delete-btn');
        if (deleteButton) {
            const row = deleteButton.closest('tr'); // 클릭한 버튼이 속한 행(TR)
            if (confirm('이 항목을 정말 삭제하시겠습니까?')) {
                row.remove(); // 행 삭제
                updateRowNumbers(); // 행 삭제 후 'No' 열 갱신
            }
            return; // 모달이 열리지 않도록 여기서 중단
        }

        // '삭제' 버튼이 아닌, 행(TR)의 다른 부분을 클릭한 경우
        const clickedRow = e.target.closest('tr.data-row');
        if (clickedRow) {
            openModal(clickedRow); // 편집 모달 열기
        }
    });
}

// 모달의 '저장' 버튼 클릭 이벤트
if (saveChangesBtn) {
    saveChangesBtn.addEventListener('click', function() {
        if (currentRow) {
            const cells = currentRow.getElementsByTagName('td');
            
            // 폼의 새 데이터로 테이블 셀(TD) 내용 업데이트
            cells[1].innerText = document.getElementById('editName').value;
            cells[2].innerText = document.getElementById('editNumber').value;
            cells[3].innerText = document.getElementById('editAsset').value;
            // 상태 셀은 getStatusSpan 함수를 통해 HTML(색상 span)을 다시 생성
            cells[4].innerHTML = getStatusSpan(document.getElementById('editStatus').value);
            cells[5].innerText = document.getElementById('editLastDate').value;
            cells[6].innerText = document.getElementById('editNextDate').value;
            cells[7].innerText = document.getElementById('editManager').value;

            closeModal(); // 모달 닫기
        }
    });
}

// 모달의 '취소' 버튼 클릭 이벤트
if (closeModalBtn) {
    closeModalBtn.addEventListener('click', closeModal);
}

// 모달 바깥의 어두운 배경 클릭 시 닫기
if (editModal) {
    editModal.addEventListener('click', function(e) {
        // e.target이 모달의 배경(editModal 자신)일 때만 닫기
        if (e.target === editModal) {
            closeModal();
        }
    });
}

// --- 5. 페이지 로드 시 초기화 ---
// defer 속성으로 <script>를 불렀기 때문에 DOMContentLoaded가 필수는 아니지만,
// 명시적으로 DOM이 로드된 후에 실행되도록 하는 것이 더 안전합니다.
document.addEventListener('DOMContentLoaded', function() {
    // null 체크 추가 (HTML 요소들을 찾지 못했을 경우 오류 방지)
    if (tableBody && addRowBtn && editModal && closeModalBtn && saveChangesBtn && editForm) {
        updateRowNumbers(); // 페이지 로드 시 'No' 열 번호 매기기
    } else {
        console.error("필수 HTML 요소를 찾을 수 없습니다. ID를 확인해주세요.");
    }
});

