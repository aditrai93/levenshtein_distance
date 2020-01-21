# levenshtein_distance
#Edit distance
w1="bright"
w2="knight"
li1=[]
counter=0
def lowest(n1,n2,n3):
    l=0
    if n1<n2<n3 or n1<n3<n2:
        l=n1
    elif n2<n1<n3 or n2<n3<n1:
        l=n2
    else:
        l=n3
    return l
    
for i in range(len(w1)+2):
    li=[]
    for j in range(len(w2)+2):
        if i==0:
            if j==0:
                li.append("")
            elif j==1:
                li.append(str(0))
            else:
                li.append(w1[j-2])
        elif i==1:
            if j==0:
                li.append(str(j))
            elif j==1:
                li.append(str(0))
            else:
                li.append(str(j-1))
        elif i>1:
            if j==0:
                li.append(w2[counter])
                counter=counter+1
            elif j==1:
                li.append(str(i-1))
            else:
                li.append(str(2))
                            
        
    li1.append(li)
for i in range(0,len(w1)+2):
    for j in range(0,len(w2)+2):
        if i>1:
            if j>1:
                s1=int(li1[i-1][j])+1
                s2=int(li1[i][j-1])+1
                if li1[0][j]==li1[i][0]:
                    s3=int(li1[i-1][j-1])+0
                else:
                    s3=int(li1[i-1][j-1])+1
                low=lowest(s1,s2,s3)
                li1[i][j]=str(low)
for i in li1:
    print(i,"\n")
        
        

