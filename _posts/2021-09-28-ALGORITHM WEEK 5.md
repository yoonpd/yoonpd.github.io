# 알고리즘 5주차 정리

## Heap Sort - Advanced Sorting Algoritm

### Tree

- 계층적 구조를 표현하는 자료 구조
- 트리의 표현
  - Root / Leaf / Internal Node
    - Leaf : 말단 노드
    - Internal Node : Root와 Leaf를 제외한 노드
  - Edge / Branch / Link : 노드를 연결한 선
  - Height / Depth
  - Parent / Child / Siblings
  - Subtree
  - Level n : n은 Root에서 특정 노드까지 연결된 간선의 개수
- **노드가 N개인 트리는 항상 N-1개의 링크를 갖는다.**
- 트리는 위(Root)에서 아래(Leaf)로 읽는다.<br>

- **이진 트리**
  - <span style="color:red">각 노드가 최대 두 개의 자식</span>을 갖는 트리
  - 완전 이진 트리(Complete Binary Tree)와 포화 이진 트리(Perfect Binary Tree)가 있음
  - Complete Binary Tree
    - 마지막 레벨을 제외하고 모든 레벨이 완전히 채워져 있는 트리
    - 마지막 레벨은, 노드가 <span style="color:blue">**왼쪽에서 오른쪽**</span>으로 채워져야 함
    - 배열을 이용하여 표현 가능 → 비어있는 부분이 없기 때문에, **순차적으로 표현할 수 있음**
  - Perfect Binary Tree
    - 마지막 레벨까지 모든 레벨이 완전히 채워져 있는 트리 <br>

### (Binary) Heap Tree

- 우선순위 큐를 위하여 만들어진 자료구조 <br>→ 최댓값이나 최솟값을 빠르게 찾을 수 있는 구조

- <span style="color:red">**완전 이진 트리의 일종**</span>으로 <span style="color:blue">**Heap Property**</span>를 만족해야 함
  1. **Max heap property : 부모는 자식보다 크거나 같다.** <br>
     →루트 노드가 최댓값을 가짐 <br>
     → Subtree의 루트 노드는 해당 subtree에서의 최댓값을 가짐
  2. **Min heap property : 부모는 자식보다 작거나 같다.**<br>
     →루트 노드가 최솟값을 가짐 <br>
     → Subtree의 루트 노드는 해당 subtree에서의 최솟값을 가짐
  
- 반정렬 상태(느슨한 정렬 상태) 유지

- 어떤 데이터로부터 만들 수 있는 힙 트리는 유일하게 존재하지 않는다.<br>

- Heap은 1차원 배열로 표현할 수 있음 → **완전 이진 트리이기 때문**

  - 루트 노드 A[1]
  - A[i]의 부모 = A[ floor(i/2) ]
  - A[i]의 왼쪽 자식 = A[2i] → Always Even
  - A[i]의 오른쪽 자식 = A[2i+1] → Always Odd <br>
    

- **MAX-Heapify**

  - 힙이 아닌 완전 이진 트리를 힙으로 만드는 것

  - Max heap property를 만족시키게 된다면, 최종적으로 Max Heap이 될 것임

    1. 부모 노드의 값이 자식 노드의 값들보다 작다면 자식 노드 중 큰 값과 부모 노드의 값과 바꾼다.
    2. 이를 루트부터 차례대로 진행을 한다.

  - Pseudo Code

    ```c
    MAX-HEAPIFY(A, i){
      if there is no child of A[i]
        return;
      
      k ← index of the biggest child of i;
      
      if A[i] >= A[k]
        return;
      
      swap(A[i] and A[k]);
      MAX-HEAPIFY(A, k);				// Recursive
    }
    ```

    → root 노드에 대한 heapify는 MAX-HEAPIFY(1)을 호출하면 된다. <br>

- **Heap Sort**

  - Max-Heapify가 된 트리에서

    1. Extract Max value : Remove the maximum element from a heap (Root Node)
    2. Restore the structure to a heap : Re-Heapify
    3. Iterate 1~2 <br>

  - Pseudo code

    ```c
    BUILD-MAX-HEAP(A)
    for i ← length[A] downto 2
      do swap(A[1], A[i])			// 말단 노드의 값을 루트 노드로 삽입
        heap-size[A] ← heap-size[A] - 1
        MAX-HEAPIFY(A, 1)
    ```

    <br>



### Priority Queue

- Queue와 비슷한 형태이지만, 우선순위가 높은 값이 먼저 튀어나오는 형태
- 연산 종류
  1. Insert : 완전 이진 트리에 맞도록 마지막에 삽입한 뒤, 부모와 값을 비교하여 swap 연산을 Recursive하게
  2. Extract-Max : 루트의 값을 빼내고, 자식 값과 비교를 통해 swap 연산을 Recursive하게

<br>

### Counting Sort

- Non-comparison Sort : 정렬할 데이터에 대한 **사전 지식을 이용**하는 방법 <br>
  → 지금까지의 방법은 Comparison Sort
- 예시) <br>
  → 다음 5 이하 자연수 데이터들을 오름차순으로 정렬하세요. <br>
  → {1, 3, 5, 3, 4, 2, 5, 1, 2, 1, ...}
  - 각 값의 누적(count)를 셈
  - 이후 각 누적 값만큼 출력을 하게 되면 정렬이 됨
