# Task for Python

## Problem - Inverted ROT-N Cipher

Cipher is an element of cryptography - which is essentially a set of rules to
encrypt (and decrypt) a message (encrypted message). One example of such cipher
is the [ROT13](http://practicalcryptography.com/ciphers/classical-era/rot13/)
cipher, which is: shift each alphabet of the message forward by 13 counts. By
this rule `a` becomes `n`, `b` becomes `o` and so on:

```
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
│ │ │ │ │ │ │ │ │ │ │ │ │ │ │ │ │ │ │ │ │ │ │ │ │ │
▼ ▼ ▼ ▼ ▼ ▼ ▼ ▼ ▼ ▼ ▼ ▼ ▼ ▼ ▼ ▼ ▼ ▼ ▼ ▼ ▼ ▼ ▼ ▼ ▼ ▼
N O P Q R S T U V W X Y Z A B C D E F G H I J K L M
```

The cipher we discuss will have the number of shifts as a variable, rather than
sticking to 13 like ROT-13 does (hence the name ROT-N).

Another simple example of cipher is the Atbash cipher, where the letters of the
alphabet are reversed. The goal of this problem is to create a two functions
`inv_rotn_encrypt()` and `inv_rotn_decrypt()` - one for encrypting, one for
decrypting. The arguments for these functions is as follows:

```python
inv_rotn_encrypt(message, shift)
# message is the message to be encrypted
# shift is the number of letters to shift
inv_rotn_decrypt(secret, shift)
# secret is the encrypted message to be decrypted to obtain original message
# shift is the number of shifts used to encrypt the original message
```

Encrypting process:

1. Shift the letters of the message by the number specified by `shift` argument.
   (note that the shift argument should always be an integer, as the concept of
   fractional shift is absurd).
2. Reverse the order of the letters obtained from previous step.
3. Return the encrypted message obtained thus.

Decrypting process:

1. Reverse the order of characters in the given encrypted message.
2. Shift backwards the string obtained from previous step by the specified
   `shift` number.
3. Return the decrypted message obtained thus.

An example workflow would be:

```python
message = 'bobody'
print("Message: ", message)
secret = inv_rotn_encrypt(message, 17)
print("Encrypted message: ", secret)
message_again = inv_rotn_decrypt(secret, 17)
print("Decrypted message: ", message_again)
```

Output:

```
Message: bobody
Encrypted message: pufsfs
Decrypted message: bobody
```

## Submission procedure

1. Fork this repository.
2. Create a directory named `python-01`.
3. Make a copy of `template.ipynb` from `template` directory inside `python-01` directory
   with your roll number e.g. `ph19b003.ipynb` (in lowercase).
3. Add responses (1 function in Problem 1, and 2 functions in Problem 2) in
   the jupyter notebook you copied.
4. Commit the changes, push to your account.
5. Create a pull request with title format `rollnumber_name`. It should be in
   all lowercase, and replace spaces in name with `-`.
6. And that's it!