#Шестнадцатиричные чётные числа, не превышающие 2048в10. Вывести числа и их количество. Максимальное число вывести прописью.

import re
slovar = {0:'ноль',1:'один',2:'два',3:'три',4:'четыре',5:'пять',6:'шесть',7:'семь',8:'восемь',9:'девять',\
     'A':'десять','B':'одинадцать','C':'двенадцать','D':'тринадцать','E':'четырнадцать','F':'пятнадцать'}
maxim = "0"
s_maxim = ''
kolich = 0
file = open("text.txt", "r")
marks = '''!()-[]{};?@#$%:'"\,./^&amp;*_'''
while True:
    a = file.readline().split()
    if not a:
        print('\nКонец файла')
        break
    for j in a:
        for x in j:
            if x in marks:
                j = j.replace(x, "")
        res = re.findall(r'[1-7]?[0-9 A-F]?[02468ACE]{1}', j)
        if len(res) == 1:
            if len(j) == len(res[0]) and len(j)>0:
                print(res[0], end=" ")
                kolich += 1
                if int(res[0], 16) > int(maxim, 16):
                    maxim = res[0]
                    s_maxim = j
if maxim == 0:
    print('В файле нет чисел, удовлетворяющих условию')
else:
    print('Количество:', kolich)
    print('Максимальное число:', end=' ')
    for j in range(len(maxim)):
        for l in slovar:
            if str(l) == maxim[j]:
                print(slovar[l], end=' ')
                break
