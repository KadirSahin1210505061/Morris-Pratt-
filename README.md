# Morris-Pratt-
Morris-Pratt algoritması, bir metinde verilen bir kalıbı aramak için kullanılan bir algoritmadır.

public static int MorrisPratt(string text, string pattern)
{
    int n = text.Length;
    int m = pattern.Length;

    int[] next = ComputeNext(pattern);

    int i = 0;
    int j = 0;

    while (i < n)
    {
        if (text[i] == pattern[j])
        {
            i++;
            j++;

            if (j == m)
            {
                return i - j;
            }
        }
        else if (j > 0)
        {
            j = next[j];
        }
        else
        {
            i++;
        }
    }

    return -1;
}

private static int[] ComputeNext(string pattern)
{
    int m = pattern.Length;
    int[] next = new int[m];

    int i = 0;
    int j = -1;

    next[0] = -1;

    while (i < m - 1)
    {
        if (j == -1 || pattern[i] == pattern[j])
        {
            i++;
            j++;
            next[i] = j;
        }
        else
        {
            j = next[j];
        }
    }

    return next;
}

 Algoritmaların amacı, bir problemi çözmek için adım adım bir yöntem sağlamaktır. Morris-Pratt algoritması, bir metinde verilen bir kalıbı aramak için kullanılır. Bu algoritma, Boyer-Moore algoritmasına benzer, ancak farklı bir yaklaşım kullanır. Morris-Pratt algoritması, daha az karşılaştırma yapar ve daha az bellek kullanır. Algoritmanın çalışma şekli şu şekildedir:
Bir next dizisi hesaplanır. Bu dizi, eşleşme olmadığında kalıbın hangi konumuna geri dönüleceğini belirtir.
Text dizesinde kalıp aranır.
Eğer karakterler eşleşirse, i ve j değerleri artırılır. Eğer j kalıbın uzunluğuna eşit olursa, kalıp bulunmuştur ve i-j konumunda dönüş yapılır.
Eğer karakterler eşleşmezse, j değeri next[j] ile değiştirilir. Bu, kalıbın önceki bir konumuna geri dönülmesini sağlar.
Algoritmaların çalışma zamanı analizi, bir algoritmanın ne kadar hızlı veya yavaş olduğunu belirlemek için kullanılır. En iyi, en kötü ve ortalama sınırları belirlemek için big O gösterimi kullanılır. Morris-Pratt algoritması için en kötü durum O(m+n) ve en iyi durum O(n) olarak hesaplanır
