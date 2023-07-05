### Hi there 👋

<!--
**ezoerdem/ezoerdem** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->

import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
import seaborn as sns

df = pd.read_excel("Dataset.xlsx")

plt.figure(figsize=(14,7))
plt.style.use('seaborn-darkgrid')
sns.lineplot(x="Perimeter" , y="Compactness" , hue="Class" , data=df)
plt.title('Perimeter vs Compactness', fontsize = 20)
plt.show()

plt.figure(figsize=(10,8))
sns.scatterplot(x=df.Perimeter , y=df.Compactness , hue=df.Class )
plt.show()

plt.figure(figsize=(18,6))
sns.swarmplot(x="Class" , y = "Perimeter" ,data=df)
plt.show()

plt.figure(figsize=(18,6))
sns.swarmplot(x="Class" , y = "Compactness" ,data=df)
plt.show()
