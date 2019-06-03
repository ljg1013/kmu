산업체특강 (2019.3.18)

1. 특강명 : 분산시스템을 이용하여 대규모 그래프에 존재하는 모든 삼각형 찾아내기

2. 특강 강사님 : 박하명 교수님

3. 특강내용

(1) 분산시스템이란?
- 여러 대의 컴퓨터를 가지고 high speed network를 만드는 시스템
- Hadoop, spark를 이용
- 작은 규모가 아닌 대규모 그래프를 대상으로 함(굉장히 많은 노드와 에지)

  -> (점 3개)삼각형을 찾는다.

(2) Graphs are Everywhere
- friendship network : 사람이 노드가 되고 두사람이 친구이면 에지가 연결이 된다.
- phoncall Network : 통화기록이 있으면 연결한다.
- knowledge base : 관련된 지식들이 연결된다.
- internet, www : 페이지와 페이지들이 연결된다.

(3) 어떻게 하면 그래프 속에 있는 패턴이나 anomalies를 찾을 수 있을까?
- spam(ad) users, DDos attack, communities

  -> 그래픽 데이터에서 이것들을 분류
- triangle enumeration

  -> 그래프에 존재하는 모든 삼각형을 찾아낸다.

- Application 1. facebook의 유저를 분석-> spam(ad) users를 찾음
  
  -> 가운데가 ‘나’, (친구)그룹으로 나눠진다. 그룹 안에 있는 사람들은 다 서로 친구이다.
     그룹과 그룹 간에는 친구가 아니다.

  -> normal uwer with many triangles
  
  -> spammer with few triangle
  
  -> fake user with massive triangles

- Application 2. DDos attack detection
  
  -> Botnet Attack / Triangle Expectation of relationship

- Application 3.Community detection
  
  -> Clustering coefficient = # triangles / #possible triangles
  
  -> Clustering coefficient가 높은 것들을 먼저 골라내고 나머지 지움
  
  -> connected component 구분 가능해진다.
  
  -> 커뮤니티를 찾을 수 있다.

(4) Graphs are enormous
- 페이스북은 1억명 / 웹은 1tillion
  
  -> 분산시스템을 사용해야한다.
  
  -> 어떤 데이터가 분산파일 시스템에 저장되고
  
  -> 노드와 에지를 불러온다(subgraph)
  
  -> 다시 분산시스템에 저장한다.

(5) 문제점
- massive intermediate data
- intermediate data size가 너무 커서 running time이 길다. ->줄여야한다.

(6) 해결방안
- 에지를 복사하고 에지를 grouping한다 + Shuffling
- Shuffling과 sorting하는 데에 오래 걸림
  
  -> data줄여야함
  
  -> 색깔에 따라 에지 블락을 나눈다.
  
  -> sorting작업이 없어지고 기존보다 훨씬 빠르게 작업할 수 있다.

(7) 결론
- problem : Triangle Enumeration
  
  -> Application : Finding patterns and anomalies
- Distributed Algorithms
  
  -> Basic Distributed Algorithm : Vertex Coloring
  
  -> Multi-Round Algorithm : Resolve shuffled data explosion
  
  -> Pre-partitioning based Algorithm : shrink shuffled data size
- Future work
  
  -> Generalization to Subgraph Enumeration
  
  -> Triangle Enumeration on a Heterogeneous Cluster

