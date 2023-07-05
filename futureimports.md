- 👋 Hi, I’m @ezoerdem
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
ezoerdem/ezoerdem is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import pandas as pd
import seaborn as sns
from matplotlib import pyplot as plt
from sklearn.model_selection import train_test_split
from imblearn.over_sampling import SMOTE
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import plot_confusion_matrix
from matplotlib import pyplot
from sklearn.model_selection import RandomizedSearchCV
df = pd.read_excel("Dataset.xlsx")
X = df.drop('Class', axis=1)
y = df['Class']
sm = SMOTE(random_state=2)
X_m, y_m = sm.fit_resample(X, y)
Xm_train, Xm_test, ym_train, ym_test = train_test_split(X_m, y_m,test_size=0.25, random_state=0)
Xm_train, Xm_val, ym_train, ym_val = train_test_split(Xm_train, ym_train, test_size=0.25, random_state=0)
clf = RandomForestClassifier(random_state=0)
clf.fit(Xm_train, ym_train)
feature_imp=pd.Series(clf.feature_importances_,index=X.columns).sort_values(ascending=False)
sns.barplot(x=feature_imp, y=feature_imp.index)
# Add labels to your graph
plt.xlabel('Feature Importance Score')
plt.ylabel('Features')
plt.title("Visualizing Important Features")
plt.legend()
plt.show()
