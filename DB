from difflib import SequenceMatcher
def similar(a, b):
    return SequenceMatcher(None, a, b).ratio()

import Stemmer
stemmer = Stemmer.Stemmer('russian')
import re

z = open('/home/apple/Interaction_vidal/Molecule_Interactions_from_vidalDB.txt', 'r', encoding='utf8')
vidal = open('/home/apple/Interaction_vidal/MoleculeID_toMolecule.txt', 'r', encoding='utf8')
outFile = open('/home/apple/Interaction_vidal/output.txt', 'w', encoding='utf8')
lines = z.readlines()
vid = vidal.readlines()

for line in lines:
    ln = re.sub(',','',line)
    ln = re.sub(';','',ln)
    ln = re.sub('\.','',ln)
    ln = ln.split()
    st = []
    for word in ln:
        st.append(stemmer.stemWord(word))
    tmp = []
    for row in vid:
        rw = row.split()
        row1 = stemmer.stemWord(rw[-1])
        for sym in st:
            sim = similar(row1, sym)
            if sim > 0.9 and row1 != st[2] and sym != 'кислот':
                tmp.append(rw[0])
                tmp.append(row1)
                tmp.append(line)
                print(' '.join(tmp), file=outFile)
                break;

z.close()
vidal.close()
outFile.close()
