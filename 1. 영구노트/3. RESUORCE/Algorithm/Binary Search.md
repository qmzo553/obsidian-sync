### 주제 : 이분 탐색

### 날짜 : 2024-04-25 17:43
----
### 메모
> Binary Search
> 
> 작동 원리
> 	- 정렬된 배열 : binary search를 사용하기 전에, 데이터는 반드시 정렬되어 있어야 한다.
> 	- 중간 요소 확인 : 배열의 중간 위치를 찾고 . 그값이 타겟 값과 같은지 확인한다.
> 	- 범위 조정 
> 		1. 중간 요소의 값보다 타겟 값이 작으면, 검색 범위를 중간 요소의 왼쪽 부분으로 좁힌다.
> 		2. 중간 요소의 값보다 타겟 값이 크면, 검색 범위를 중간 요소의 오른쪽 부분으로 좁힌다.
> 	- 반복 또는 종료 : 위 과정을 값이. 찾아질 때까지 또는 검색 범위가 더 이상 없을 때까지 반복한다.
> 
> 장점
> 	- 효율적이다.
> 	- 큰 데이터 집합에 대해서도 빠르게 작동하며, 시간 복잡도는 O(log n)이다.
> 
> 단점
> 	- 배열이 정렬되어 있어야만 사용할 . 수있다.
> 	- 동적인 데이터 집합에서는 추가, 삭제 등의 작업이 빈번히 일어날 경우, 유지 관리가 비효울적일 수 있다.
```java
public class BinarySearch {  
  
    public static int binarySearch(int[] arr, int target) {  
        int left = 0;  
        int right = arr.length - 1;  
  
        while(left <= right) {  
            int mid = left + (right - left) / 2;  
  
            if(arr[mid] == target) {  
                return mid;  
            }  
  
            if(arr[mid] < target) {  
                left = mid + 1;  
            } else {  
                right = mid - 1;  
            }  
        }  
  
        return -1;  
    }  
  
    public static void main(String[] args) {  
        int[] sortedArray = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };  
        int target = 7;  
  
        int result = binarySearch(sortedArray, target);  
        if(result == -1) {  
            System.out.println("Element not found");  
        } else   {  
            System.out.println("Element found at index " + result);  
        }
    }  
}
```

### 출처(참고 문헌)
-

### 연결 문서
-
