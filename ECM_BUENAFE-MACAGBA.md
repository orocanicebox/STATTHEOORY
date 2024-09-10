<h1>ECM_BUENAFE_MACAGBA</h1>

<p> </p>


```python

import itertools as it 

r=["Robredo 1","Robredo 2"]
m=["Marcos 1","Marcos 2","Marcos 3","Marcos 4"]

s=r+m
s


```




    ['Robredo 1', 'Robredo 2', 'Marcos 1', 'Marcos 2', 'Marcos 3', 'Marcos 4']




```python
com = list(it.combinations(s,4) )

# Print the obtained permutations 
for i in com:
    print(i)
    

print(len(com)," Samples")

```

    ('Robredo 1', 'Robredo 2', 'Marcos 1', 'Marcos 2')
    ('Robredo 1', 'Robredo 2', 'Marcos 1', 'Marcos 3')
    ('Robredo 1', 'Robredo 2', 'Marcos 1', 'Marcos 4')
    ('Robredo 1', 'Robredo 2', 'Marcos 2', 'Marcos 3')
    ('Robredo 1', 'Robredo 2', 'Marcos 2', 'Marcos 4')
    ('Robredo 1', 'Robredo 2', 'Marcos 3', 'Marcos 4')
    ('Robredo 1', 'Marcos 1', 'Marcos 2', 'Marcos 3')
    ('Robredo 1', 'Marcos 1', 'Marcos 2', 'Marcos 4')
    ('Robredo 1', 'Marcos 1', 'Marcos 3', 'Marcos 4')
    ('Robredo 1', 'Marcos 2', 'Marcos 3', 'Marcos 4')
    ('Robredo 2', 'Marcos 1', 'Marcos 2', 'Marcos 3')
    ('Robredo 2', 'Marcos 1', 'Marcos 2', 'Marcos 4')
    ('Robredo 2', 'Marcos 1', 'Marcos 3', 'Marcos 4')
    ('Robredo 2', 'Marcos 2', 'Marcos 3', 'Marcos 4')
    ('Marcos 1', 'Marcos 2', 'Marcos 3', 'Marcos 4')
    15  Samples



```python
nr = 0
nm = 0
total_prob_r = 0
total_prob_m = 0

for i in com:
    for x in r:
        if x in i:                
            nr += 1
    for y in m:
        if y in i:
            nm += 1
            
    prob_r = nr / len(i)
    prob_m = nm / len(i)
    
    total_prob_r += prob_r
    total_prob_m += prob_m
    
    print(i, "Probability: Robredo:", prob_r, "Marcos:", prob_m)
    
    # Reset counters for the next iteration
    nr = 0
    nm = 0

# Calculate the average distribution across all elements in com
average_prob_r = total_prob_r / len(com)
average_prob_m = total_prob_m / len(com)

print("Average Probability - Robredo:", average_prob_r)
print("Average Probability - Marcos:", average_prob_m)

```

    ('Robredo 1', 'Robredo 2', 'Marcos 1', 'Marcos 2') Probability: Robredo: 0.5 Marcos: 0.5
    ('Robredo 1', 'Robredo 2', 'Marcos 1', 'Marcos 3') Probability: Robredo: 0.5 Marcos: 0.5
    ('Robredo 1', 'Robredo 2', 'Marcos 1', 'Marcos 4') Probability: Robredo: 0.5 Marcos: 0.5
    ('Robredo 1', 'Robredo 2', 'Marcos 2', 'Marcos 3') Probability: Robredo: 0.5 Marcos: 0.5
    ('Robredo 1', 'Robredo 2', 'Marcos 2', 'Marcos 4') Probability: Robredo: 0.5 Marcos: 0.5
    ('Robredo 1', 'Robredo 2', 'Marcos 3', 'Marcos 4') Probability: Robredo: 0.5 Marcos: 0.5
    ('Robredo 1', 'Marcos 1', 'Marcos 2', 'Marcos 3') Probability: Robredo: 0.25 Marcos: 0.75
    ('Robredo 1', 'Marcos 1', 'Marcos 2', 'Marcos 4') Probability: Robredo: 0.25 Marcos: 0.75
    ('Robredo 1', 'Marcos 1', 'Marcos 3', 'Marcos 4') Probability: Robredo: 0.25 Marcos: 0.75
    ('Robredo 1', 'Marcos 2', 'Marcos 3', 'Marcos 4') Probability: Robredo: 0.25 Marcos: 0.75
    ('Robredo 2', 'Marcos 1', 'Marcos 2', 'Marcos 3') Probability: Robredo: 0.25 Marcos: 0.75
    ('Robredo 2', 'Marcos 1', 'Marcos 2', 'Marcos 4') Probability: Robredo: 0.25 Marcos: 0.75
    ('Robredo 2', 'Marcos 1', 'Marcos 3', 'Marcos 4') Probability: Robredo: 0.25 Marcos: 0.75
    ('Robredo 2', 'Marcos 2', 'Marcos 3', 'Marcos 4') Probability: Robredo: 0.25 Marcos: 0.75
    ('Marcos 1', 'Marcos 2', 'Marcos 3', 'Marcos 4') Probability: Robredo: 0.0 Marcos: 1.0
    Average Probability - Robredo: 0.3333333333333333
    Average Probability - Marcos: 0.6666666666666666



```python
import pandas as pd

# Initialize lists to store the data
data = []

nr = 0
nm = 0
total_prob_r = 0
total_prob_m = 0

for i in com:
    for x in r:
        if x in i:
            nr += 1
    for y in m:
        if y in i:
            nm += 1
    
    prob_r = nr / len(i)
    prob_m = nm / len(i)
    
    total_prob_r += prob_r
    total_prob_m += prob_m
    
    # Append row data to the list
    data.append([i, prob_r, prob_m])
    
    nr = 0
    nm = 0

# Create a pandas DataFrame from the data
df = pd.DataFrame(data, columns=["Comment", "Robredo Probability", "Marcos Probability"])

# Print the table
print(df)

# Calculate and print the average distribution
average_prob_r = total_prob_r / len(com)
average_prob_m = total_prob_m / len(com)
print("\nAverage Probability - Robredo:", average_prob_r)
print("Average Probability - Marcos:", average_prob_m)

```

                                           Comment  Robredo Probability  \
    0   (Robredo 1, Robredo 2, Marcos 1, Marcos 2)                 0.50   
    1   (Robredo 1, Robredo 2, Marcos 1, Marcos 3)                 0.50   
    2   (Robredo 1, Robredo 2, Marcos 1, Marcos 4)                 0.50   
    3   (Robredo 1, Robredo 2, Marcos 2, Marcos 3)                 0.50   
    4   (Robredo 1, Robredo 2, Marcos 2, Marcos 4)                 0.50   
    5   (Robredo 1, Robredo 2, Marcos 3, Marcos 4)                 0.50   
    6    (Robredo 1, Marcos 1, Marcos 2, Marcos 3)                 0.25   
    7    (Robredo 1, Marcos 1, Marcos 2, Marcos 4)                 0.25   
    8    (Robredo 1, Marcos 1, Marcos 3, Marcos 4)                 0.25   
    9    (Robredo 1, Marcos 2, Marcos 3, Marcos 4)                 0.25   
    10   (Robredo 2, Marcos 1, Marcos 2, Marcos 3)                 0.25   
    11   (Robredo 2, Marcos 1, Marcos 2, Marcos 4)                 0.25   
    12   (Robredo 2, Marcos 1, Marcos 3, Marcos 4)                 0.25   
    13   (Robredo 2, Marcos 2, Marcos 3, Marcos 4)                 0.25   
    14    (Marcos 1, Marcos 2, Marcos 3, Marcos 4)                 0.00   
    
        Marcos Probability  
    0                 0.50  
    1                 0.50  
    2                 0.50  
    3                 0.50  
    4                 0.50  
    5                 0.50  
    6                 0.75  
    7                 0.75  
    8                 0.75  
    9                 0.75  
    10                0.75  
    11                0.75  
    12                0.75  
    13                0.75  
    14                1.00  
    
    Average Probability - Robredo: 0.3333333333333333
    Average Probability - Marcos: 0.6666666666666666



```python

```
