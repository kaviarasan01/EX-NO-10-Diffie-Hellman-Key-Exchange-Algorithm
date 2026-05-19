# EX-NO-10-Diffie-Hellman-Key-Exchange-Algorithm

## AIM:
To Implement Diffie Hellman Key Exchange Algorithm 

## Algorithm:

1. Diffie-Hellman Key Exchange is used for securely sharing a secret key between two parties over an insecure channel.

2. Initialization: Agree on a large prime number \( p \) and a primitive root \( g \) modulo \( p \) (both are public values).

3. Key Exchange Process: 
   - Each party selects a private key and calculates their public key using the formula \( g^{\text{private key}} \mod p \).
   - Each party then shares their public key with the other.

4. Secret Key Computation: 
   - Each party computes the shared secret key using the received public key and their own private key.

5. Security: The difficulty of computing discrete logarithms ensures that the shared key remains secure even if public values are intercepted.

## Program:

```c
#include <stdio.h>
#include <math.h>

// Function to perform modular exponentiation
long long powerMod(long long base, long long exp, long long mod) {
    long long result = 1;
    base = base % mod;
    while (exp > 0) {
        if (exp % 2 == 1)  // if exp is odd
            result = (result * base) % mod;
        exp = exp / 2;
        base = (base * base) % mod;
    }
    return result;
}

int main() {
    long long p, g, a, b, A, B, secretA, secretB;

    // Publicly agreed values
    printf("Enter a prime number p: ");
    scanf("%lld", &p);
    printf("Enter primitive root g modulo p: ");
    scanf("%lld", &g);

    // Private keys chosen by Alice and Bob
    printf("Enter Alice's private key: ");
    scanf("%lld", &a);
    printf("Enter Bob's private key: ");
    scanf("%lld", &b);

    // Public keys
    A = powerMod(g, a, p);
    B = powerMod(g, b, p);

    printf("\nAlice's public key: %lld", A);
    printf("\nBob's public key: %lld", B);

    // Shared secret computation
    secretA = powerMod(B, a, p);
    secretB = powerMod(A, b, p);

    printf("\n\nShared secret computed by Alice: %lld", secretA);
    printf("\nShared secret computed by Bob: %lld\n", secretB);

    if (secretA == secretB)
        printf("\n✅ Key exchange successful! Shared secret established.\n");
    else
        printf("\n❌ Key exchange failed. Secrets do not match.\n");

    return 0;
}


```

## Output:

<img width="1105" height="959" alt="image" src="https://github.com/user-attachments/assets/2469e5a6-f2a4-4977-bb17-511c2a2d8ebd" />


## Result:
  The program is executed successfully

