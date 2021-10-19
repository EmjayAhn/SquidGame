# GA4 개요

## Ga4란?

구글 애널리틱스(Google Analytics, GA)의 4번째 업데이트 버전으로, 기존의 GA 대비 **분석에 대한 관점, 방향성, 사용성 등의 여러 측면에서 변화됨**. 

- GA4에 추가된 주요 기능
  - 무료 빅쿼리 연동 (최대 일 1TB 쿼리 무료)
  - 사이트 중심이 아닌 고객여정 흐름 중심의 데이터 측정
  - 자동수집 이벤트 추적
  - 앱 + 웹 통합 분석 지원



GA4에서 업데이트된 기능들

![](/Users/jeon-yujin/Downloads/image-1.png)

# Big Query 데이터

## 빅쿼리란?

GA에서 수집되는 **웹/앱 로그 데이터를** **빠른 SQL 쿼리로 제공하는 데이터 웨어하우스**

## 빅쿼리를 활용한 데이터 추출

- UI 에서 쿼리로 추출

- API로 추출

  ```python
  import pydata_google_auth
  from google.cloud import bigquery
  import datetime
  
  CUSTOMER = 'customer'
  CUSTOMER_INFO = {
      'customer': {
          'project': 'customer_project',
          'query': """
                  SELECT * FROM customer_project.table
                  WHERE _table_suffix BETWEEN '{}' AND '{}';
                  """.format(report_date, report_date)
      },
  }
  
  report_date = datetime.datetime.today().strftime('%Y%m%d')
  
  # bigquery로 데이터 추출
  try:
      project = CUSTOMER_INFO.get(CUSTOMER)['project']
      query = CUSTOMER_INFO.get(CUSTOMER)['query']
  
      cred = pydata_google_auth.get_user_credentials(
          ['https://www.googleapis.com/auth/bigquery']
      )
      client = bigquery.Client(project=project, 
                          credentials=cred,
                          )
  
      df = client.query(query).to_dataframe()
      
  except KeyError as e:
      raise e
  ```



## 빅쿼리 데이터 개요 

### 주요 필드

- **event_names**

  - GA4에서 기본으로 추적되는 이벤트 + 사용자가 정의하고 심어놓은 이벤트
    - ex)'first_visit', 'session_start', 'page_view', '메인/스크롤', 'scroll', 'user_engagement', '상세보기/스크롤', 'view_item'

- **event_params**

  - 각각의 이벤트가 갖는 파라미터

    - ex) 
      page_view
      ['page_title', 'session_engaged', 'ga_session_number', 'entrances', 'debug_mode', 'ga_session_id', 'engaged_session_event', 'page_location', 'page_referrer', 'ignore_referrer', 'source', 'medium', 'campaign', 'term'] 

      상세보기/스크롤
      ['page_title', 'ga_session_number', '스크롤 깊이', '스크롤 방향', 'ga_session_id', 'engagement_time_msec', 'debug_mode', 'session_engaged', 'page_location', '스크롤 단위', 'engaged_session_event', 'page_referrer', 'ignore_referrer', 'source', 'campaign', 'medium']



### 데이터 분석 및 활용방안

- 분석 프로세스 
  - 비궈리 데이터 추출 → 1차 데이터 정제 (unnesting) → 분석 목적 및 내용 정의 → 데이터 정제 및 분석 → 시각화

- 분석 포인트 정의
  1. 분석 목적 정의 
     - 비즈니스의 현황 파악 및 문제점 발견 -> 해결방안, 개선포인트 도출
  2. 분석 내용 정의
     1. 제품 페이지별 구매전환율/고객 이탈율/engagement
     2. 매체별 유입 대비 구매전환율
     3. 고객들의 행동 (스크롤, 체류시간, 클릭 등)
     4. 고객여정(퍼널) 단계별 이탈율
     5. 크로스구매 상품
     6. 메인 고객의 인구통계정보
     7. 등...
  3. 분석 및 시각화
  4. 개선안 도출
     1. 이탈율이 높은 페이지 ui/ux 개선
     2. 타겟팅 조정
     3. 광고 메인 상품 교체
     4. 랜딩페이지 교체
     5. 등.....

