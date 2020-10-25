# howtostart
Just trying


grass growing
high


ADT Array
     object : index의 각 값에 대하여 집합 item에 속한 한 값이 존재하는 <index, value>쌍의 집합. 
                  index는 일차원 또는 다차원 유한 순서 집합이다. 예를 들면, 1차원의 경우 {0, …., n-1}과 
                  2차원 배열{(0,0), (0,1), (0,2), (1,0), (1,1), (1,2), (2,0), (2,1), (2,2)} 등이다.
     functions : 모든 A∈Array, i∈index, x∈item, j, size∈integer
           Array create(j, list) ::= return j차원의 배열
                                                여기서 list는 i번째 원소가 i번째 차원의 크기인
                                                 j-tuple이며 item들은 정의 되지 않았음.
           item Retrieve(A, i) ::= if (i∈index)
                                                        return 배열 A의 인덱스 i값과 관련된 항목.
                                                else return 에러.
           Array Store(A, i, x) ::= if (i ∈ index)
end Array

레코드 타입의 경우 타입이 다른 데이터 묶음을 그룹화 하는 것으로, 배열처럼 같은 타입의 데이터 묶음을 연속된 메모리 위치의 집합으로 구현하는 것과는 차이가 있다. 
