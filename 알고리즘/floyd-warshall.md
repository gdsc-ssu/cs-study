
  

## πνλ‘μ΄λ-μμΒ μκ³ λ¦¬μ¦

- λͺ¨λ  μ΅λ¨ κ²½λ‘λ₯Ό κ΅¬νλ μκ³ λ¦¬μ¦
- DPμκ³ λ¦¬μ¦μ μνλ μκ³ λ¦¬μ¦
    - λΈλμ κ°μκ° N κ°λΌκ³  ν  λ, N λ² λ§νΌ λ¨κ³λ₯Ό λ°λ³΅νλ©° μ νμμ λ§κ² 2μ°¨μ λ¦¬μ€νΈλ₯Ό κ°±μ νκΈ° λλ¬Έμ!   
       
<br/>

## πνλ‘μ΄λ-μμ VS λ€μ΅μ€νΈλΌ


**λ€μ΅μ€νΈλΌ μκ³ λ¦¬μ¦(Dijkstra)**

- νλμ μ μ μμ λΆν° λ€λ₯Έ λͺ¨λ  μ μ μΌλ‘μ μ΅λ¨ κ²½λ‘λ₯Ό κ΅¬ν΄μ€

<aside>

>π‘ κ°μ₯ μ μ λΉμ©μ νλμ© μ ννμ!
    
  <br/>

</aside>

**νλ‘μ΄λ-μμ μκ³ λ¦¬μ¦**

- λͺ¨λ  μ μ μμ λ€λ₯Έ λͺ¨λ  μ μ μΌλ‘μ μ΅λ¨ κ²½λ‘λ₯Ό κ΅¬ν΄μ€

<aside>

>π‘ βκ±°μ³κ°λ μ μ βμ κΈ°μ€μΌλ‘ μ΅λ¨ κ±°λ¦¬λ₯Ό κ΅¬ν΄λ³΄μ!

</aside>
<br/>
<br/>

![https://k.kakaocdn.net/dn/mUTHI/btqZkq0vzfU/kMTM4smM75w7a9qHqFEllk/img.png](https://k.kakaocdn.net/dn/mUTHI/btqZkq0vzfU/kMTM4smM75w7a9qHqFEllk/img.png)

[https://loosie.tistory.com/146](https://loosie.tistory.com/146) μ¬μ§ μΆμ²!
<br/>
<br/>

## πλμ κ³Όμ 



- λͺ¨λ  λΈλ κ°μ μ΅λ¨κ±°λ¦¬λ₯Ό κ΅¬ν΄μΌ νλ―λ‘ **2μ°¨μ μΈμ  νλ ¬** κ΅¬μ±
- λΌμ΄λλ§λ€ κ° κ²½λ‘μμ **μλ‘μ΄ μ€κ° λΈλλ‘ μ¬μ©ν  μ μλ λΈλλ₯Ό μ ν**νκ³ , λ μ§§μ κΈΈμ΄λ₯Ό μ ννμ¬ μ€μ΄λ κ³Όμ  λ°λ³΅

<aside>

>π‘ Floyd-Warshall μκ³ λ¦¬μ¦μ μ νμ
>
> **$$
>D^{k}[i][j]=minimum(D^{(k-1)}[i][j],D^{(k-1)}[i][k]+D^{(k-1)}[k][j])
>$$**
>
> β **βiμμ jλ‘ κ°λ μ΅μ λΉμ©β** κ³Ό **βiμμ kλ₯Ό κ±°μ³ jλ‘ κ°λ λΉμ©β** μ λΉκ΅νμ¬, λ μμ κ°μΌλ‘ κ°±μ 

</aside>
<br/>

## πλμ μμ 


**βμ°κ²°λμ§ μμ κ°μ β** μ μμμ ν° κ°(λ¬΄ν)μ, **βμκΈ° μμ β** μΌλ‘ κ°λ λΉμ©μ 0 κ°μ λ£μ΄μ€



![https://k.kakaocdn.net/dn/bBc94M/btrGB41I9Us/jTMIsW3SkFjesbIYEMkxj1/img.png](https://k.kakaocdn.net/dn/bBc94M/btrGB41I9Us/jTMIsW3SkFjesbIYEMkxj1/img.png)

**kλ² λΈλλ₯Ό κ²½μ μ§λ‘** μΌμ ν, μ΅λ¨ κ±°λ¦¬ νμ΄λΈ κ°±μ ν΄μ€

---

![https://k.kakaocdn.net/dn/bN72MI/btrGB5ffoJb/A7Aml9jUMqrFXZAfbBndTK/img.png](https://k.kakaocdn.net/dn/bN72MI/btrGB5ffoJb/A7Aml9jUMqrFXZAfbBndTK/img.png)

![https://k.kakaocdn.net/dn/cmGAm0/btrGARBMjIQ/L07rPYtomu0KmdMXrsJck0/img.png](https://k.kakaocdn.net/dn/cmGAm0/btrGARBMjIQ/L07rPYtomu0KmdMXrsJck0/img.png)

![https://k.kakaocdn.net/dn/0n5w6/btrGzv0ymiU/CaJkktyzDjVGkfA9mWl8Uk/img.png](https://k.kakaocdn.net/dn/0n5w6/btrGzv0ymiU/CaJkktyzDjVGkfA9mWl8Uk/img.png)

![https://k.kakaocdn.net/dn/7RV1f/btrGzdy4hY9/DnjFxkfvs37noZewWFZbi0/img.png](https://k.kakaocdn.net/dn/7RV1f/btrGzdy4hY9/DnjFxkfvs37noZewWFZbi0/img.png)

<br/>

### πμ½λ μ λ¬Έ(Pseudo)

  
  #

- W[i][j]: μ μ  iμμ jλ‘ κ°λ μ΄μμ μ κ°μ€μΉ
- D[i][j]: μ μ  iμμ jλ‘ κ°λ μ΅λ¨κ²½λ‘
- k: κ²½μ μ§

```java
void floyd(int n, const number W[][], number D[][])
{
	index i,j,k;
	D = W
	for(k = 1;k <= n;k++)
		for(i = 1;i <= n;i++)
			for(j = 1;j <= n;j++)
				D[i][j] = minimum(D[i][j],D[i][k]+D[k][j]);
}
```
