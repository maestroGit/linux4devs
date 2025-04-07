
**awk** (Aho, Weinberger, Kernighan)

awk és una eina molt potent per processar i manipular textos, especialment per extreure i manipular columnes dins de fitxers estructurats.​

Sintaxi:​

```sh
awk '{acció}' fitxer​
```

Exemple per imprimir la primera columna:​
```sh
awk '{print $1}' fitxer.txt
```
