import csv

with open('/content/SFU_constructiveness_toxicity_corpus.csv','rt') as constructiveness_labels:
  with open('/content/labeled data.csv', mode='w') as new_labels:
    data = csv.reader(constructiveness_labels)
    # relabeling as 'non blocked' if the comment is constructive
    counter = 0
    for row in data:
      if row[6] == 'yes': # 6 is constructiveness row
        csv.writer(new_labels).writerow(row + ['non blocked'])
      elif row[6] == 'no' and toxic(row[8]) == False:
        csv.writer(new_labels).writerow(row + ['non blocked'])
      elif row[6] == 'no' and toxic(row[8]) == True:
        csv.writer(new_labels).writerow(row + ['blocked'])
        print(row[5])
        counter = counter + 1
      else:
        csv.writer(new_labels).writerow(row + ['blocked/non blocked comment'])
    print(counter)

# 1044 comentarios; 38 bloqueados según toxic

def toxic(string): # if the string contains a '4' then it should be somehow toxic
  for char in string:
    if char == '4':
      very_toxic = True
      break  
    else:
      very_toxic = False
  return very_toxic

def toxic2(string): # this is useless because there is actually no comment labeled with a level '4' of toxicity
  if string == '4':
    very_toxic = True
    return very_toxic
