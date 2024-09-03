# FFT


The Fast Fourier Transform (FFT) is an efficient algorithm to compute the Discrete Fourier Transform (DFT) and its inverse. The DFT is used to analyze the frequency components of a discrete signal.


Discrete Fourier Transform (DFT)
Given a sequence of n complex numbers x_0, x_1, ..., x_(n-1), the DFT produces another sequence X_0, X_1, ..., X_(n-1), which represents the frequency domain of the original sequence. The DFT is defined as:
X_k = sum_{j=0}^{n-1} x_j * exp(-2*pi*i*j*k/n)  for k = 0, 1, ..., n-1
where:
X_k is the k-th frequency component.
x_j is the j-th time-domain sample.
exp(-2*pi*i*j*k/n) is a complex exponential (often called a "twiddle factor").

Time Complexity of DFT
The naive computation of the DFT requires O(n^2) operations because it involves a double summation: one loop over k (for each frequency component) and one loop over j (for each time sample).


The FFT is an algorithm that reduces the time complexity of computing the DFT from O(n^2) to O(n*log(n)). The most common form of the FFT is the Cooley-Tukey algorithm. The Cooley-Tukey algorithm works by recursively breaking down the DFT of a sequence of length n into smaller DFTs of lengths n/2, leveraging the symmetry and periodicity properties of the complex exponentials.

Divide:
Split the sequence x_0, x_1, ..., x_(n-1) into two smaller sequences:
Even-indexed elements: x_0, x_2, x_4, ..., x_(n-2)
Odd-indexed elements: x_1, x_3, x_5, ..., x_(n-1)

Conquer:
Recursively compute the DFT of the even-indexed sequence (call this E_k) and the odd-indexed sequence (call this O_k).

Combine:
Use the results of the smaller DFTs to compute the DFT of the original sequence:
For k = 0 to n/2-1:
X_k = E_k + exp(-2*pi*i*k/n) * O_k
X_(k+n/2) = E_k - exp(-2*pi*i*k/n) * O_k
Here, the complex exponential exp(-2*pi*i*k/n) is a twiddle factor that combines the even and odd parts.

Base Case:
The recursion stops when the sequence length is 1, at which point the DFT of a single element is just the element itself.


Time Complexity of FFT
The FFT algorithm reduces the time complexity to O(n*log(n)), which is a significant improvement over the O(n^2) time required by the naive DFT.
