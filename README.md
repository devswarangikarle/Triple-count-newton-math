# Triple-count-newton-math
Newton likes to play with numbers. He is given two integers N and K. Find the number of triples (a, b, c) of positive integers not greater than N such that a+b, b+c, and c+a are all multiples of K. The order of a, b, and c does matter, and some of them can be the same. Input The input line contains N and K separated by space.  

def count_triples(N, K):
    residue_count = [0] * K
   
    for a in range(1, N + 1):
        residue_count[a % K] += 1
    
    total_count = 0
    
    for r in range(K):
        if r * 2 % K == 0: 
            total_count += residue_count[r] * residue_count[(K - r) % K] * residue_count[r]
    
    return total_count

N, K = map(int, input().split())

print(count_triples(N, K))
