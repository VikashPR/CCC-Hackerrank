# R 101 : Eat Less
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
``` python
n = int(input())
c = []
while not c:
    c = list(map(int,input().split()))
c.sort(reverse = True)
result = 0
for i in range(n):
    result += c[i]*(2**i)
print(result)
```

# R 102 : Highest Possible Product
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
``` python
n = int(input())
arr = list(map(int, input().split()))

# Sort the array in non-decreasing order
arr.sort()

# Product of the last three numbers
prod1 = arr[n-1] * arr[n-2] * arr[n-3]

# Product of the first two (negative) numbers and the last number
prod2 = arr[0] * arr[1] * arr[n-1]

max_prod = max(prod1, prod2)
print(max_prod)

```

# R 103 : Pucca and The Card Game
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
import math

n = int(input())
a = list(map(int, input().split()))

i = 0
j = n - 1
k = 1
b = [0, 0]

while i <= j:
    if k == 1:
        k = 0
    else:
        k = 1
    if a[i] < a[j]:
        b[k] += a[j]
        j -= 1
    else:
        b[k] += a[i]
        i += 1

if b[0] >= b[1]:
    print("Pucca")
else:
    print("Garu")
```

# R 104 : Greedy Rayinshi
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

``` python
n = int(input())
cards = list(map(int, input().split()))

# Initialize scores for both players
rayinshi_score = 0
neechea_score = 0

# Rayinshi starts the game
turn = 'rayinshi'

# Keep playing the game until all cards have been picked
while cards:
    # Pick the card with the larger number
    if cards[0] > cards[-1]:
        picked_card = cards.pop(0)
    else:
        picked_card = cards.pop()

    # Add the picked card to the respective player's score
    if turn == 'rayinshi':
        rayinshi_score += picked_card
        turn = 'neechea'
    else:
        neechea_score += picked_card
        turn = 'rayinshi'

# Output the final scores
print(rayinshi_score, neechea_score)
````