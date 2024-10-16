[https://www.programmieraufgaben.ch/](https://www.programmieraufgaben.ch/)

## Liste von Strings vertikalisieren. (Zeichenketten)

Schreibe ein Programm, das eine gegebene Liste von Strings vertikal auf der Konsole ausgibt.

Zwischen den Buchstaben sollte ein Leerzeichen sein.

Beispiel:

liste=['programmier', 'aufgaben', '.ch']

Ausgabe:<br>
p a .<br>
r u c<br>
o f h<br>
g g  <br>
r a  <br>
a b  <br>
m e  <br>
m n  <br>
i    <br>
e    <br>
r<br>


```python
l=['programmier', 'aufgaben', '.ch']
print("\n".join([" ".join([b[c] for b in [a+" "*(len(max(l,key=len))-len(a)) for a in l]]) for c in range(len(max(l,key=len)))]))
```

```python
def vertical_output(lst):
    max_len = max(len(word) for word in lst)
    
    for i in range(max_len):
        line = []
        for word in lst:
            if i < len(word):
                line.append(word[i])
            else:
                line.append(" ")
        print(" ".join(line))

# Example
lst = ['programmier', 'aufgaben', '.ch']
vertical_output(lst)
```

## Zeichen verschieben in String (Zeichenketten)

Gegeben sei der String s="#---------".

Lasse das "#" durch die Striche wandern und lasse das Ergebnis in der Konsole anzeigen.

Sollte wie folgt aussehen:<br>
#---------<br>
-#--------<br>
--#-------<br>
---#------<br>
----#-----<br>
-----#----<br>
------#---<br>
-------#--<br>
--------#-<br>
---------#<br>

```python
s="#---------"
print("\n".join([s]+["-"*i+s[:-i] for i in range(1,10)]))
```

```python
def wander_hash(s):
    for i in range(len(s)):
        print("-" * i + "#" + "-" * (len(s) - i - 1))

# Example
s = "#---------"
wander_hash(s)
```
