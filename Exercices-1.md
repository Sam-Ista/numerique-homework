---
jupytext:
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.17.3
kernelspec:
  name: python3
  display_name: Python 3 (ipykernel)
  language: python
---

```{code-cell} ipython3
import numpy as np
def zebre(n):
    Tab=np.zeros((n,n))
    Tab[:,1::2]=1
    return Tab 
```

```{code-cell} ipython3
zebre(6)
```

```{code-cell} ipython3
def damier(n,p):
    tab=np.zeros((n,n))
    if p==False : 
        tab[::2,1::2]=1
        tab[1::2,::2]=1
    else : 
        tab[::2,::2]=1
        tab[1::2,1::2]=1
    return tab 
```

```{code-cell} ipython3
damier(4,False)
```

```{code-cell} ipython3
damier(4,True)
```

```{code-cell} ipython3
def block_checkers(n,k):
    I,J=np.indices((n,n))
    return np.repeat((np.repeat((I+J)%2,k,axis=0)),k,axis=1)
    
```

```{code-cell} ipython3
block_checkers(4,3)
```

```{code-cell} ipython3
I,J=np.indices((2*4+1,2*4+1))
print(I+J)
print(J)
print(I)
```

```{code-cell} ipython3
def escalier(n):
    I,J=np.indices((2*n+1,2*n+1))
    M=I+J
    M1=M[:n+1,:n+1]
    for j in range(1,n+1):
        for i in range(1,n+2):
            M[i-1,2*n+1-j]=M1[i-1,j-1]
    for j in range(2*n+1):
        for i in range(n+1,2*n+1):
            M[i,j]=M[2*n-i,j]
    return M
```

```{code-cell} ipython3
escalier(4)
```

```{code-cell} ipython3
def escalier2(n):
    I,J=np.indices((2*n+1,2*n+1))
    M=I+J
    M1=M[:n+1,:n+1]
    M[:n+1,n:2*n+1]=M1[:,::-1]
    M[n+1:,:]=M[:n,:]
    M[n+1:,:]=M[:n:-1,:]
    return M
```

```{code-cell} ipython3
escalier2(4)
```
