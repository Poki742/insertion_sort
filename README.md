# insertion_sort<br>
Java 삽입 정렬<br>
## 삽입 정렬(insertion sort) 알고리즘 개념 요약<br>
손안의 카드를 정렬하는 방법과 유사하다.<br>
새로운 카드를 기존의 정렬된 카드 사이의 올바른 자리를 찾아 삽입한다.<br>
새로 삽입될 카드의 수만큼 반복하게 되면 전체 카드가 정렬된다.<br>
자료 배열의 모든 요소를 앞에서부터 차례대로 이미 정렬된 배열 부분과 비교 하여,<br>자신의 위치를 찾아 삽입함으로써 정렬을 완성하는 알고리즘
매 순서마다 해당 원소를 삽입할 수 있는 위치를 찾아 해당 위치에 넣는다.<br>
## 장점과 단점
### 장점<br>
알고리즘 구현이 간단하고 단순하다.<br>
이미 정렬되어 있는 경우 매우 효율적이다.<br>
### 단점<br>
배열이 길수록 효율성이 떨어진다.<br>
## 예시
![image](https://user-images.githubusercontent.com/126844692/223327403-be51e62b-0107-4bbd-8fdd-43bd68c0359f.png)
## 설명<br>
### 1회전<br>
두 번째 자료인 5를 Key로 해서 그 이전의 자료들과 비교한다.<br>
Key 값 5와 첫 번째 자료인 8을 비교한다.<br>
8이 5보다 크므로 8을 5자리에 넣고 Key 값 5를 8의 자리인 첫 번째에 기억시킨다.<br>
### 2회전<br>
세 번째 자료인 6을 Key 값으로 해서 그 이전의 자료들과 비교한다.<br>
Key 값 6과 두 번째 자료인 8을 비교한다.<br>8이 Key 값보다 크므로 8을 6이 있던 세 번째 자리에 기억시킨다.<br><br>
Key 값 6과 첫 번째 자료인 5를 비교한다.<br>5가 Key 값보다 작으므로 Key 값 6을 두 번째 자리에 기억시킨다.<br><br>
### 3회전<br>
네 번째 자료인 2를 Key 값으로 해서 그 이전의 자료들과 비교한다.<br>
Key 값 2와 세 번째 자료인 8을 비교한다.<br>8이 Key 값보다 크므로 8을 2가 있던 네 번째 자리에 기억시킨다.<br><br>
Key 값 2와 두 번째 자료인 6을 비교한다.<br>6이 Key 값보다 크므로 6을 세 번째 자리에 기억시킨다.<br><br>
Key 값 2와 첫 번째 자료인 5를 비교한다.<br>5가 Key 값보다 크므로 5를 두 번째 자리에 넣고 그 자리에 Key 값 2를 기억시킨다.<br><br>
### 4회전<br>
다섯 번째 자료인 4를 Key 값으로 해서 그 이전의 자료들과 비교한다.<br>
Key 값 4와 네 번째 자료인 8을 비교한다.<br>8이 Key 값보다 크므로 8을 다섯 번째 자리에 기억시킨다.<br><br>
Key 값 4와 세 번째 자료인 6을 비교한다.<br>6이 Key 값보다 크므로 6을 네 번째 자리에 기억시킨다.<br><br>
Key 값 4와 두 번째 자료인 5를 비교한다.<br>5가 Key 값보다 크므로 5를 세 번째 자리에 기억시킨다.<br><br>
Key 값 4와 첫 번째 자료인 2를 비교한다.<br>2가 Key 값보다 작으므로 4를 두 번째 자리에 기억시킨다.<br><br>
## for문<br>

package 자바;<br>
import java.util.Arrays;<br>
public class insertion_sort {<br>
	static int[] nums;<br>
	
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		nums = new int[10];
		for (int i = 0; i < 10; i++) {
			nums[i] = (int) (Math.random() * 10);
		}
		System.out.println("<정렬 전>");
		System.out.println(Arrays.toString(nums));
		
		for(int i = 1; i < nums.length; i++) {
			// 현재 선택된 원소의 값을 임시 변수에 저장해준다.
			int temp = nums[i];
			// 현재 원소를 기준으로 이전 원소를 탐색하기 위한 index 변수.
			int prev = i - 1;
			// 현재 선택된 원소가 이전 원소보다 작은 경우까지만 반복. 단, 0번째 원소까지만 비교한다.
			while(prev >= 0 && nums[prev] > temp) {
				// 현재 선택된 원소가 현재 탐색중인 원소보다 작다면, 해당 원소는 다음 인덱스로 미뤄버린다.
				nums[prev + 1] = nums[prev];
				// 다음 대상 원소를 탐색한다.
				prev--;
			}
			// 탐색이 종료된 지점에 현재 선택되었던 변수의 값을 삽입해준다.
			nums[prev + 1] = temp;
		}
		
		System.out.println("<정렬 후>");
		System.out.println(Arrays.toString(nums));
	}

}

## 출력 결과<br>
<정렬 전><br>
[7, 1, 0, 5, 1, 1, 2, 2, 0, 3]<br>
<정렬 후><br>
[0, 0, 1, 1, 1, 2, 2, 3, 5, 7]<br>
## 실행된 이미지<br>






