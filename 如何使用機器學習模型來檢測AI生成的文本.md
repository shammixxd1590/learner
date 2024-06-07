import numpy as np
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.model_selection import train_test_split
from sklearn.svm import SVC
from sklearn.metrics import classification_report

# 假設有兩個文本數據集：human_texts和ai_texts
human_texts = ["這是人類寫的文本。", "另一個人類寫的例子。"]
ai_texts = ["這是AI生成的文本。", "另一個AI生成的例子。"]

# 標記數據集
texts = human_texts + ai_texts
labels = [0] * len(human_texts) + [1] * len(ai_texts)

# 使用TF-IDF進行特徵提取
vectorizer = TfidfVectorizer()
X = vectorizer.fit_transform(texts)
y = np.array(labels)

# 分割訓練集和測試集
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# 訓練支持向量機（SVM）分類器
clf = SVC()
clf.fit(X_train, y_train)

# 預測並打印結果
y_pred = clf.predict(X_test)
print(classification_report(y_test, y_pred))

#這個範例使用了支持向量機（SVM）進行文本分類，來區分人類創作的文本和AI生成的文本。可以根據需要調整和擴展此範例，以應對更複雜的檢測需求。
