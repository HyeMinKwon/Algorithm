기본 개념

## dfs
- 구현 : stack(재귀), 인접행렬 또는 인접리스트
- 더이상 나아갈 길이 보이지 않을 만큼 깊이 찾아가면서 탐색한다. 나아길 길이 존재하지 않으면 이전의 위치로 돌아와 찾아가지 않은 다른 길로 뻗어 나가면서 탐색해나간다

-인접행렬
public static void dfs(int[][] a, boolean[] c, int v) { 
  int n = a.length - 1; 
  c[v] = true; System.out.print(v + " "); 
  for (int i = 1; i <= n; i++) { 
    if (a[v][i] == 1 && !c[i]) { dfs(a, c, i); } 
  } 
}

-스택
public static void dfs(int[][] a, boolean[] c, int v, boolean flag) {
		Stack<Integer> stack = new Stack<>();
		int n = a.length - 1;

		stack.push(v);
		c[v] = true;
		System.out.print(v + " ");

		while (!stack.isEmpty()) {
			int vv = stack.peek();

			flag = false;

			for (int i = 1; i <= n; i++) {

				if (a[vv][i] == 1 && !c[i]) {
					stack.push(i);
					System.out.print(i + " ");

					c[i] = true;
					flag = true;
					break;
				}
			}
			if (!flag) {
				stack.pop();
			}
		}
	}

1. 간선으로연걸,not방문 정점 찾기
2. 조건에 맞는 정점찾으면 stack에 push and break-> break하면서 dfs탐색 진행
3. 연결된간선 없고, 방문x면 pop


bfs : 큐를 사용(최단경로, 임의경로 탐색에 사용)
- 간선으로 연결되어있고, 방문하지 않은 정점 찾기
- 조건에 맞으면 큐에 넣기
(dfs는 break문을 걸어씨만 얘는 모두 다 큐에 넣어 너비기준탐색)
- 모든 경우를 탐색-> 최단 경로에 적합

둘이 공통점 - 모두 정점을 한 번만 탐색. 탐색 여부를 확인하기 위한 check배열 필요


=================================
인접행렬
인접리스트: 존재하는 만큼만 탐색
