#### 첫 번째 접근 (X)

    # 각각의 자릿수를 비교하여 이중리스트에 각 문장의 index를 따서, 다른 글자의 갯수를 세고 리스트에 넣는다.
    # 다른 갯수가 적립된 리스트가 a 문장이 나머지 문장들과 비교했을 때 다른 글자의 갯수를 표현한다.
    # a행 내부에 숫자를 모두 더하면, 최소 Hamming Distance의 합이 된다.
    # -> 접근 자체가 틀린 것 같다.
    
    # 문제를 잘못 이해했나? 🥲
    
    # + for문이 너무 많다.

```python
N, M = map(int, input().split())

dna_list = [ ' '.join(input()).split() for _ in range(N)]

counts = 0
count_list = [ [0] * N for _ in range(N) ]

for n in range(N):
    for n2 in range(N):
        counts = 0
        for m in range(M):
            if n != n2:
                # print(n, n2, m)
                if dna_list[n][m] != dna_list[n2][m]:
                    # print(f'{dna_list[n][m]}와 {dna_list[n2][m]}의 값이 같다.')
                    counts += 1
        count_list[n][n2] = counts
print(counts, '횟수')
print(count_list, 'list')

for start in range(len(count_list)):
    for end in range(len(count_list)):
        m = count_list[0][0]
        if m < count_list[start][end]:
            m = count_list[start][end]
            m_start = start
            m_end = end
    # print(dna_list[m_start][m_end])

result = 0

for a in range(N):
    m1 = 0
    for b in range(N):
        m1 += count_list[a][b]
    if m1 > result:
        result = m1
        print(dna_list[a])
print(result)



```

