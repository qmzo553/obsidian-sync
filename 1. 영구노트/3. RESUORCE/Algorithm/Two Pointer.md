### 주제 : 투포인터에 대해서

### 날짜 : 2024-05-12 22:40
----
### 메모
> Two Pointer
> 	- 배려이나 리스트와 같은 연속적인 공간에서 두 개의 포인터를 이용하여 문제를 해결하는 알고리즘이다.
> 	- 주로 정렬된 배열에서 특정 합을 찾거나, 연속 부분 배열의 최대합을 구하는 등의 문제에 사용된다.
> 
> 주요 사용 사례
> 	- 정렬된 배열에서 두수의 합 찾기
> 	- 연속 부분 배열의 특성 만족 찾기
```java
public class TwoPointer {  
  
    public static void main(String[] args) {  
        int[] arr = {2, 4, 7, 11, 15, 20};  
        int target = 22;  
  
        int[] result = twoSumSorted(arr, target);  
  
        if(result[0] != -1) {  
            System.out.println(result[0] + " " + result[1]);  
        } else {  
            System.out.println(-1);  
        }    }  
  
    public static int[] twoSumSorted(int[] arr, int target) {  
        int left = 0, right = arr.length - 1;  
  
        while(left < right) {  
            int sum = arr[left] + arr[right];  
            if(sum == target) {  
                return new int[]{left, right};  
            } else if(sum < target) {  
                left++;  
            } else {  
                right--;  
            }  
        }  
  
        return new int[]{-1, -1};  
    }  
}
```

### 출처(참고 문헌)
-

### 연결 문서
-
