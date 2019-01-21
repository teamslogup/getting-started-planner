# getting-started-planner

## 개요
슬로그업 내에서 작성하는 기획 문서 규칙입니다. 슬로그업에서는 기능정의서 문서를 YAML or JSON 문법에 의거하여 작성하고 있습니다. 따라서 기획문서를 작성하거나 읽으려는 사람은 반드시 해당 내용을 숙지해야 합니다.

## 문서의 종류
1. 기능정의서: 기능정의서는 서비스의 각 도메인별 / 메뉴별 / 레이아웃별 핵심기능과, 부가적인 설명을 명시 해 놓은 문서입니다. 기존 기능정의서 (Function definition) 문서는 일반적으로 엑셀파일등을 이용하여 작성하였습니다. 하지만 슬로그업 내에서는 생산성 향상을 위하여 불필요한 그리드와 형태를 제거하고 심플하고 명료한 내용 전달을 위해 YAML 문법을 도입하였습니다.

2. 프로세스정의서: 프로세스정의서(process definition)는 일반적으로 diagram을 활용하여 문서를 표현합니다. 하지만 diagram을 이용한 문서는 별도로 flowchart라는 이름을 이용하여 작성하며, 슬로그업 내 프로세스정의서는 개발시 bdd의 근간이 되는 문서라고 할 수 있습니다. 따라서 프로세스정의서 또한 YAML문법을 이용하여 작성합니다.

3. 플로우차트: 기존 프로세스정의서에 flow개념을 명시적으로 더한 문서입니다. keynote, excel 및 LucidChart 등을 이용하여 표기를 합니다. 별도로 정해진 형태는 없습니다.

4. 도메인다이어그램: 도메인을 표현한 다이어그램입니다. 이또한 플로우차트와 마찬가지로 특별히 정해진 형태는 없습니다. 다만 반드시 도메인의 유비쿼터스랭귀지 (이하 UL)을 잘 표현하도록 작성하여야 하며, 모든 UL은 일관성이 있어야 합니다. 즉 하나의 UL이 여러의미를 포함해서는 안되며 만일 UL이 특정 집합을 의미하는 것이라면 집합에 속하는 상세한 도메인의 UL이 별도로 존재해야 합니다.

5. 리소스정의서: 리소스정의서는 마이크로서비스 간 통신이 필요한 인터페이스를 정의합니다. 마이크로서비스 간 통신은 presentation layer에서 이뤄지나, 예외적으로 application layer의 인터페이스가 있는 경우도 있습니다. 리소스정의서 또한 YAML문법으로 이뤄져 있습니다.

6. 인포메이션아키텍쳐: 인포메이션아키텍쳐는 서비스의 사이트맵을 알려주는 문서입니다. 기본적으로 YAML 문법을 이용하여 작성하며 예를들면 다음과 같습니다.
	```
	CRM 안드로이드 앱:
	  - 네비게이션:
	    - 나의정보
	    - 로그아웃
	  - 제품관리
	  - 재고관리
	``` 
	이 외 다른 툴을 이용하여 문서를 작성할 수 도 있습니다.
	
7. 와이어프레임: 와이어프레임 문서는 기능정의서 내용을 기준으로 mock 화면을 와이어프레임을 이용하여 정의한 문서입니다. 발사믹목업, 키노트, 파워포인트 등 다양한 문서형태를 활용할 수 있습니다.  
와이어프레임이 Backoffice 화면과 같은 특정한 패턴이 있는 경우라면 fd와 같은 문서와 비슷하게 표현이 가능합니다. 예를들면 다음과 같습니다.
	```
	거래처:
	  - lay_contents:
	    - lay_header:
	      - 제목: 거래처
	    - lay_body:
	      - lay_table:
	        - lay_header:
		  - 거래처명 검색
		  - 회사형태 필터
	        - lay_body:
                  - 거래처명
                  - 회사형태
                  - 업종
                  - 업태
                  - 대표자
                  - btn_거래내역보기
                - lay_footer:
		  - pagination
	```
	해당 문서는 기능정의서와 같은 필드명에 문서의 비쥬얼적인 구조를 명시한 문서입니다. 즉 lay_라는 접두어로 시작하면 문서의 레이아웃(block) 요소를 의미하게 되며 contents는 header, body, footer등으로 이뤄질 수 있다는 것을 유추할 수 있습니다. 또한 body내에서는 다시 다른 block요소가 올 수 있으며 여기서는 table이라는 레이아웃요소가 추가되었습니다. (해당 문서는 layout의 lay와 block요소를 동일하게 보고 있습니다.)
	마지막으로 btn_ 이라는 버튼을 의미하는 접두어를 사용하여 버튼을 표시하였습니다. 해당 접두어는 필요시 약속에 의하여 계속 추가가 가능합니다.
	이런식으로 각 약속된 문서 형태를 이용하여 text로 기술한 와이어프레임이 있을 수 있습니다.  (단 이러한 방식의 단점은 복잡한 레이아웃의 경우 불필요하게 depth나 구조가 어려워 질 수 있다는 점입니다.)
	
## 문서별 상세 설명
### 기능정의서
기능정의서는 \*fd\*.yaml 문서의 형태입니다. tab을 이용하여 depth를 구분하며 주석을 이용하여 부가설명을 적습니다.

주석의 경우 다음 2가지 형태로 이용이 가능합니다.
1. 분기처리
2. 부가설명

분기처리의 경우 주석이 기능정의서 내용 위쪽에 위치합니다. 예를들면 다음과 같습니다.
```
거래처:
  - 회사형태:
    - 법인
    - 개인사업자
    - 개인
  #법인 or 개인사업자인 경우
  - 사업자등록번호 #대쉬(-)는 따로 저장하지 않는다.
  #개인인 경우
  - 생년월일 #프리랜서 신고등에 쓰일 생년월일이 필요하다.
```
 위 문서에서는 거래처의 형태를 위해서 회사형태, 사업자등록번호 or 생년월일의 필드가 필요하다는 의미를 표현하였습니다. 즉 최초 거래처라는 도메인을 표현하기 위해, 배열 문법을 이용하였습니다. 하지만 회사형태 표현을 위해 또다시 배열문법을 이용하여 enum 값을 표현하였습니다. 즉 회사형태라는 필드의 배열은 내부적으로 필드가 아닌 벨류를 의미합니다. 

> 해당 문서에서느 문법의 간결성을 위해 필드와 값은 따로 구분하고 있지 않습니다. 하지만 개념적 혹은 논리적으로 문서를 보고 필드와 벨류는 구분이 가능합니다.

다음으로 필드의 배열을 표현하기 위해서는 '[]' 라는 특수 기호를 이용합니다. 해당 기호는 프로그래밍 언어에서 배열을 의미하기도 합니다.
예를 들면 다음과 같습니다.
```
거래처:
  - 회사명
  - ...
  - 직원[]:
    - 이름
    - 연락처
    - 직책
```
해당 문서에서는 직원이 여럿 등록될 수 있다는 것을 표현하기 위해 필드명 옆에 []기호를 추가하였습니다. 해당 문서가 와이어프레임 문서에서는 Table로 표현될 것입니다.
또한 주석을 작성할 때의 제약사항이 몇 가지가 있습니다.
1. 주석을 의미하는 샵 이후 띄어쓰기를 하지 않습니다.
	- 올바른 주석사용: `#주석내용`
	- 잘못된 주석사용: `# 주석내용`
2. 주석을 위한 샵을 사용 시 내용에서 한칸 띄어쓰기 이후 사용합니다.
	- 올바른 주석 시작: `-거래처 #주석내용`
	- 잘못된 주석 시작: `-거래처#주석내용`
