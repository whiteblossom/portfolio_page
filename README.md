[# whiteblossom.io](https://whiteblossom.github.io/portfolio_page/)



                <div class="d-flex flex-column flex-md-row justify-content-between mb-5">
                    <div class="flex-grow-1">
                        <b>■ 프로젝트 정보</b>
                        <ul class="font-noto mt-2" style="font-size:15px; line-height: 1.6;">
                            <li><b>배경:</b> 2026년 07월 슈퍼SOL 성공 오픈을 위해 AI_Agent 환경과 서비스개발, 신한카드의 차별화된 Agent를 통한 금융 경험과 AX뱅킹 선도 기반을 마련하겠습니다. </li>
                            <li><b>목표:</b> 신한카드 대내/대외 서비스에 AI_Agent를 통해 사용자와 직원의 편의성을 향상시키고자 함</li>
                            <li><b>주요 서비스:</b> agent별 lang_graph와 llm을 통한 RAG(검색 증강 생성) 기반 답변 제공 (대외: 카드추천, 외국인 카드심사, 이벤트/쿠폰 안내, 마이카 등, 대내: 해외정산, 채권추심 등)</li>
                            <li><b>기술 스택:</b> Python, PostgreSQL, LangGraph, KL (KnowledgeLake - VectorDB)</li>
                        </ul>

                        <b>■ 수행 업무 및 주요 성과</b>
                        <ul class="font-noto mt-2" style="font-size:15px; line-height: 1.6;">
                            <li>해외정산 Agent 개발</li>
                            [ Start ]
                               │
                               ▼
                            [ Classifier ] ── (escalate=true) ──▶ [ Escalate (상담원 이관) ] ──▶ [ End ]
                               │
                               ▼ (정상 처리)
                            [ Query Processor ] : 쿼리 재작성 및 핵심 정보 추출
                               │
                               ▼
                            [ Retriever ] : OpenSearch 벡터 검색
                               │
                               ▼
                            [ Generator ] : 검색 결과를 바탕으로 4단계 섹션별 초안 생성
                               │   ├─ [0] 상황 요약 (Situation Summary)
                               │   ├─ [1] 확인된 내용 (Confirmed Details)
                               │   ├─ [2] 확인 필요 항목 (Needs Confirmation)
                               │   └─ [3] 최종 답변 (Final Answer Draft)
                               │
                               ▼
                            [ Reviewer ] : 답변 품질 검토 및 이슈(환각, 누락 등) 식별
                               │  
                               ▼  
                            [ Fixer ] : 이슈가 발생한 섹션만 타겟팅하여 재작성
                               │
                               ▼  
                            [ Send Answer ] : 최종 답변 포맷팅 및 후처리
                               │
                               ▼
                            [ End ]


                            개요
                            서비스 정의
                            해외정산 서비스는 상담뭔 분들이 고객과의 상담 중 답변하기 어려운 질의들을 보조하기 위한 서비스입니다.

                            개발 초기단계에는 상담원분들이 특히 어려워하는 '해외정산'분야에 초점이 맞추어져 있었지만 현재는 '정산'에 좀 더 초점이 맞추어져 있습니다.

                            해당 Agent는 기본적으로 두개의 mci를 가지고 통신을 진행하며 첫번째 mci는 수신시 api를 mci와 같은 기능으로 만들어 사용하고 있습니다.
                            이는 해외정산이 답변을 생성하는데 30초 이상 걸리는데 상담중 30초를 기다릴 여유가 없으므로 질의가 들어오면 첫번째 api로 수신여부를 응답한 뒤 백그라운드에서 답변을 생성하여 두번째 mci로 답변을 송신합니다.

                            <li>mcp_tool관리</li>
                            <li>마이카 Agent 초기 개발</li>

                            서비스 정의
                            해당 서비스는 신한카드 MyCar앱을 사용하는 일반 고객을 위한 실시간 AI 상담 챗봇입니다.
                            구성은 MyCar앱(프론트)과 AI 쳇봇(백엔드), 그리고 백엔드가 호출하는 외부 시스템으로 구성되어있습니다.

                            고객이 자동차 구매, 금융, 관리, 마이카 서비스 이용 방법, 이벤트 등에 대해 자연어로 물으면 사내 지식문서(RAG)를 근거로 답변하고, 관련 서비스 바로가기 버튼, 후속 추천 질문, 고객센터 연결 같은 컴포넌트를 함께 제공합니다.
                            답변은 SSE스트리밍으로 토큰단위로 화면에 흘러나옵니다.

                            프론트는 사용자의 질의를 단일 엔드포인트로 보내고 백엔드는 응답을 스트림으로 돌려줍니다. 프론트는 해당 스트림에서 답변토큰(Streaming)과 컴포넌트(Agent), 최종 통합 응답(final)을 받아 화면에 렌더링 합니다.
                            
                        </ul>
                    </div>
                </div>
