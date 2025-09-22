# Cpp
Code for leetcode

linear regression


import numpy as np
import pandas as pd

n = int(input())
data=[]
for _ in range(n):
    x,y = input().split()
    data.append({
        "feature":float(x),
        "target":float(y)
    });
                    
df = pd.DataFrame(data)
X_raw = df["feature"].values

means = X_raw.mean()
st = X_raw.std().round(2)
mini = X_raw.min().round(2)
max = X_raw.max().round(2)
X_mean = X_raw.mean()
X_std = X_raw.std()
X = (X_raw - X_mean)/X_std
Y = df["target"].values
print(df[["feature","target"]].head().to_string(index=False,header=False))
print(f"({df.shape[0]},{df.shape[1]})")

print(f"{means:.2f} {st:.2f} {mini:.2f} {max:.2f}")
print(f"{Y.mean():.2f} {Y.std():.2f} {Y.min():.2f} {Y.max():.2f}")
x_mean = np.mean(X)
y_mean = np.mean(Y)

theta_0 = 0.0
theta_1 = 0.0
alpha = 0.01
epochs = 1000
for _ in range(epochs):
    y_p = theta_0 + theta_1*X
    error = y_p - Y
    theta_0 = theta_0 - alpha * np.mean(error)
    theta_1 = theta_1 - alpha * np.mean(error * X)
y_pr = theta_0 + theta_1 * X
mse = np.mean((y_pr -Y)**2) /2
print(f"Final theta0={theta_0:.3f} | theta1={theta_1:.3f} | Final MSE={mse:.2f}")
new = np.array([150,200])
new_f = (new -X_mean )/ X_std
y1 = theta_0 + theta_1 * new_f[0]
y2 = theta_0 + theta_1 * new_f[1]
print(y1.round(2))
print(y2.round(2))






import numpy as np
import pandas as pd
n = int(input())
data = []
for _ in range(n):
    Size,Bedroom,ag,pric = input().split()
    data.append({
       "size_m2":float(Size),
       "bedrooms":float(Bedroom),
       "age_years":float(ag),
       "price_lakhs":float(pric)
    });
    
df = pd.DataFrame(data)
print(df.head().to_string(index=False,header=False))
print(f"({df.shape[0]},{df.shape[1]})")
data_m = df.to_numpy()
f_c = data_m[:,0]
s_c = data_m[:,1]
t_c = data_m[:,2]
fo_c = data_m[:,3]
print(f"{f_c.mean():.2f} {f_c.std():.2f} {f_c.min():.2f} {f_c.max():.2f}")
print(f"{s_c.mean():.2f} {s_c.std():.2f} {s_c.min():.2f} {s_c.max():.2f}")
print(f"{t_c.mean():.2f} {t_c.std():.2f} {t_c.min():.2f} {t_c.max():.2f}")
print(f"{fo_c.mean():.2f} {fo_c.std():.2f} {fo_c.min():.2f} {fo_c.max():.2f}")

feature = data_m[:,:3]
target = data_m[:, 3:]

mean_f = feature.mean(axis=0)
std_f = feature.std(axis=0)
f_std = (feature - mean_f)/std_f
X = f_std
S = f_std.shape[0]
X_prime = np.hstack((np.ones((S,1)),X))
y = target

theta = np.zeros((4,1))
alpha = 0.01
epchos = 300
for _ in range(epchos):
    y_pred = X_prime @ theta
    error = y_pred - y
    gradient = (1/S) * (X_prime.T @ error)
    theta = theta - alpha * gradient
mse_g = (1 / (2 * S)) * np.sum((X_prime @ theta - y ) ** 2)

XT = X_prime.T @ X_prime
XTy = X_prime.T @ y
theta_n = np.linalg.inv(XT) @ XTy

mse_n = (1 / (2 * S)) * np.sum((X_prime @ theta_n - y )** 2)
diff = abs(mse_g - mse_n)

theta_list = [theta[0][0],theta[1][0],theta[2][0],theta[3][0]]
print(f"Final theta=[{theta_list[0]:.3f},{theta_list[1]:.3f},{theta_list[2]:.3f},{theta_list[3]:.3f}]")
print(f"Final MSE={mse_g:.2f}")
print(f"MSE Difference={diff:.5f}")

h_a = np.array([150.0,3.0,5.0])
h_b = np.array([200.0,4.0,2.0])

ha_std = (h_a - mean_f) / std_f
hb_std = (h_b - mean_f) / std_f

ha_input = np.hstack(([1.0],ha_std))
pred_ha = ha_input @ theta

hb_input = np.hstack(([1.0],hb_std))
pred_hb = hb_input @ theta

print(f"{pred_ha[0]:.2f}")
print(f"{pred_hb[0]:.2f}")




Logistic regression-------->>>>




import numpy as np
import pandas as pd

n = int(input())
data = []
for _ in range(n):
    ex,ad = input().split()
    data.append({
        "exam_score":int(ex),
        "admitted":int(ad)
    });
    
df = pd.DataFrame(data)
X = df["exam_score"]

Y = df["admitted"]
print("First 5 rows:\n")
print(f"{df.head()}\n")
print(f"Shape (N, d): ({df.shape[0]}, {df.shape[1]})\n")
print(f"Summary statistics for exam score:")
print(f"Min: {X.min()}\nMax: {X.max()}\nMean: {X.mean():.2f}\nStd: {X.std(ddof=0):.2f}\n")

alpha = 0.01
epochs = 1000

theta0 = 0.0
theta1 = 0.0
eps = 1e-15
for _ in range(epochs):
    z = theta0 + theta1 * X
    y_c = 1 / (1 + np.exp(-z))
    
    theta_0 = np.mean(y_c - Y)
    theta_1 = np.mean((y_c - Y) * X)
    
    theta0 = theta0 -  alpha * theta_0
    theta1 = theta1 -  alpha * theta_1
    
    # loss = -np.mean(Y * np.log(y_c + eps) + (1 - Y) * np.log(1 - y_c + eps))


print(f"Final theta0: {theta0:.2f}")   
print(f"Final theta1: {theta1:.2f}") 

t = theta0 + theta1 * X
z_t = 1 / (1 + np.exp(-t))
z_sc = np.clip(z_t,1e-5,1-1e-5)

loss = -np.mean(Y * np.log(z_sc) + (1 - Y) * np.log(1 - z_sc))
print(f"Final Loss: {loss:.2f}\n\n") 

z1 = theta0 + theta1*65
r_1 = 1 / (1 + np.exp(-z1))
z2 = theta0 + theta1*155
r_2 = 1 / (1 + np.exp(-z2))
print(f"Prediction for exam_score=65: {r_1:.2f}")
print(f"Prediction for exam_score=155: {r_2:.2f}")


import numpy as np
import pandas as pd

n = int(input())
data = []
for _ in range(n):
    e1,e2,hr,a = input().split()
    data.append({
        "exam1":int(e1),
        "exam2":int(e2),
        "hours_study":int(hr),
        "admitted":int(a)
    });

df = pd.DataFrame(data)
X1 = df["exam1"]
X2 = df["exam2"]
H = df["hours_study"]
y= df["admitted"]

print("\nFirst 5 rows:")
print(f"{df.head()}\n")

print(f"Shape (N, d): ({df.shape[0]}, {df.shape[1]})\n")
print("Summary statistics:")
print(f"exam1 -> Min: {X1.min()}, Max: {X1.max()}, Mean: {X1.mean()}, Std: {round(X1.std(),2)}" )
print(f"exam2 -> Min: {X2.min()}, Max: {X2.max()}, Mean: {X2.mean():.2f}, Std: {round(X2.std(),2)}" )
print(f"hours_study -> Min: {H.min()}, Max: {H.max()}, Mean: {H.mean()}, Std: {round(H.std(),2)}\n" )

X1 = df["exam1"].values.astype(float)
X2 = df["exam2"].values.astype(float)
H = df["hours_study"].values.astype(float)

X1_mean, X1_std = X1.mean(),X1.std()
X2_mean, X2_std = X2.mean(),X2.std()
H_mean, H_std = H.mean(),H.std()

X1_sz = (X1 - X1_mean) / X1_std
X2_sz = (X2 - X2_mean) / X2_std
H_sz = (H - H_mean) / H_std

X = np.column_stack((np.ones(len(df)),X1_sz,X2_sz,H_sz))
Y = y.values.reshape(-1,1)

N = len(Y)
alpha = 0.01
epochs = 1500
theta = np.zeros((4,1))

for _ in range(epochs):
    z_pred = X @ theta 
    y_c = 1 / (1 + np.exp(-z_pred))
    
    gradient = (1/N)*((X.T) @ (y_c - Y)) 
    theta = theta - alpha * gradient
    
    
    
theta_r = theta.round(2)  
print(f"Final theta: [{theta_r[0][0]}, {theta_r[1][0]}, {theta_r[2][0]}, {theta_r[3][0]}]")

loss = -np.mean(Y * np.log(y_c + 1e-15) + (1 - Y) * np.log(1 - y_c + 1e-15))
print(f"Final Loss: {loss.round(2)}\n\n")

c1 = [72.0,80.0,11.0]
c2 = [150.0,118.0,20.0]
c1_sz = np.array([
    (c1[0] - X1_mean) / X1_std,
    (c1[1] - X2_mean) / X2_std,
    (c1[2] - H_mean) / H_std
    ])
c2_sz = np.array([
    (c2[0] - X1_mean) / X1_std,
    (c2[1] - X2_mean) / X2_std,
    (c2[2] - H_mean) / H_std
    ])

# c1_mean, c1_std = c1.mean(),c1.std()
# c2_mean, c2_std = c2.mean(),c2.std()

# c1_sz = (c1 - c1_mean) / c1_std
# c2_sz = (c2 - c2_mean) / c2_std

C1 = np.hstack(([1.0],c1_sz)).reshape(4,1)
r1 = theta.T @ C1
res1 = 1 / (1 + np.exp(-r1))

C2 = np.hstack(([1.0],c2_sz)).reshape(4,1)
r2 = theta.T @ C2
res2 = 1 / (1 + np.exp(-r2))

print(f"Prediction for (exam1=72, exam2=80, hours_study=11): {res1.item():.2f}")
print(f"Prediction for (exam1=150, exam2=118, hours_study=20): {res2.item():.2f}")



knn   ------>>>>>>


import pandas as pd
import numpy as np

n = int(input())
data = []
for _ in range(n):
    sl,sw,pl,pw,c = input().split()
    data.append({
        "SepalLength":float(sl),
        "SepalWidth":float(sw),
        "PetalLength":float(pl),
        "PetalWidth":float(pw),
        "Class":c
    });
    
df = pd.DataFrame(data)
X = df.iloc[:,0:4]
Y = df.iloc[:,4:]

def e_distance(a,b):
    return np.sqrt(np.sum((a - b) ** 2))


def knn(x_train,y_train,x_test,k):
    distance = [e_distance(x_test,X_train) for X_train in x_train.values ]
    sort_i = np.argsort(distance)
    top_l = y_train.iloc[sort_i[:k]].values.flatten()
    
    counts = {}
    for label in top_l:
        counts[label] = counts.get(label,0) + 1
    sorted_count = sorted(counts.items(), key=lambda x: x[1] , reverse=True)    
    return sorted_count[0][0]
    
def acc_score(y_true,y_pred):
    y_true = y_true.values.flatten()
    correct = sum(yt == yp for yt,yp in zip(y_true,y_pred))
    return correct / len(y_true)
    
def cross_valid(X,Y,k_neighbour):
    size = len(X)
    ind = np.arange(size)
    np.random.shuffle(ind)
    n_fold = [size // 5] * 5
    for i in range(size % 5):
        n_fold[i] += 1
        
    accuracy = []
    folds = []
    start = 0
    for fold_size in n_fold:
        end = start + fold_size
        folds.append(ind[start:end])
        start = end
        
    for i in range(5):
        
        test_i = folds[i]
        train_i = np.concatenate(folds[:i] + folds[i+1:])
        
        x_train_fold = X.iloc[train_i]
        y_train_fold = Y.iloc[train_i]
        x_test_fold = X.iloc[test_i]
        y_test_fold = Y.iloc[test_i]
        
        predictions = []
        for x in x_test_fold.values:
            pred = knn(x_train_fold,y_train_fold,x,k_neighbour)
            predictions.append(pred)
                       
        acc = acc_score(y_test_fold,predictions)
        accuracy.append(acc)
        
    return np.mean(accuracy)
    
    
    
l = len(X)

ind = np.arange(l)
np.random.seed(42)
np.random.shuffle(ind)
train_s = int(0.8*n)
train_i = ind[:train_s]
test_i = ind[train_s:]

x_train,y_train = X.iloc[train_i],Y.iloc[train_i]
x_test,y_test = X.iloc[test_i],Y.iloc[test_i]    
    
k=[1,3,5,7,9]
res = []

for i in k:
    sr = cross_valid(x_train,y_train,i)
    res.append((i,sr))
    
max_acc = max(res,key=lambda x:x[1])[1]
best_ks = [k for k, acc in res if acc == max_acc]
best_k = min(best_ks)



predict = [knn(x_train,y_train,x,best_k) for x in x_test.values]
accurac = acc_score(y_test,predict)
print("FINAL EVALUATION ON TEST SET")
print(f"Test set accuracy with k={best_k}: {accurac:.2f}")


import pandas as pd
import numpy as np

n = int(input())
data = []

for _ in range(n): 
    sl,sw,pl,pw,c = input().split()
    data.append({
        "SepalLength":float(sl),
        "SepalWidth":float(sw),
        "PetalLength":float(pl),
        "PetalWidth":float(pw),
        "Class":c
    });
    
df = pd.DataFrame(data)
X = df.iloc[:,0:4]
df.iloc[:,0:4] = df.iloc[:,0:4].astype(float)
X = (X - X.min()) / (X.max() - X.min())

Y = df.iloc[:,4:]

def mt_distance(a,b):
    return np.sum(np.abs(a - b))
    
def knn(x_train,y_train,x_test,k):
    distance = [mt_distance(x_test,row) for row in x_train.values]
    sort_i = np.argsort(distance)
    top_l = y_train.iloc[sort_i[:k]].values.flatten()
    
    counts = {}
    for label in top_l:
        counts[label] = counts.get(label , 0) + 1
        
    sorted_count = sorted(counts.items(), key = lambda x : x[1], reverse=True)
    return sorted_count[0][0]
    
def acc_score(y_true,y_pred):
    y_true = y_true.values.flatten()
    correct = sum(yt == yp for yt, yp in zip(y_true,y_pred))
    return correct / len(y_true)
    
def cross_valid(X,Y,k_neighbour):
    size = len(X)
    ind = np.arange(size)
    np.random.shuffle(ind)
    
    n_fold = [size // 5] * 5
    for i in range (size % 5):
        n_fold[i] += 1
        
    accuracy = []
    folds = []
    start = 0
    for fold_size in n_fold:
        end = start + fold_size
        folds.append(ind[start:end])
        start = end
        
    for i in range(5):
        test_i = folds[i]
        train_i = np.concatenate(folds[:i] + folds[i+1:])
        
        x_train_fold = X.iloc[train_i]
        y_train_fold = Y.iloc[train_i]
        x_test_fold = X.iloc[test_i]
        y_test_fold = Y.iloc[test_i]
        
        predictions = []
        for x in x_test_fold.values:
            pred = knn(x_train_fold,y_train_fold,x,k_neighbour)
            predictions.append(pred)
            
        acc = acc_score(y_test_fold,predictions)
        accuracy.append(acc)
        
    return np.mean(accuracy)    
        
l = len(X)
np.random.seed(42)
ind = np.arange(l)
np.random.shuffle(ind)
 
train_s = int(0.8*n)
train_i = ind[:train_s]
test_i = ind[train_s:]
 
x_train,y_train = X.iloc[train_i], Y.iloc[train_i]
x_test,y_test= X.iloc[test_i], Y.iloc[test_i]
 
k_values = [1,3,5,7,9]
res = []
 
for k in k_values:
    score = cross_valid(x_train,y_train,k)
    res.append((k,score))
    
max_acc = max(res, key=lambda x: x[1])[1]
best_ks = [k for k,acc in res if acc == max_acc]
best_k = min(best_ks)

predictions = [knn(x_train,y_train,x,best_k) for x in x_test.values]
final_a = acc_score(y_test,predictions)

print("FINAL EVALUATION ON TEST SET")
print(f"Test set accuracy with k={best_k}: {final_a:.2f}")
     
        

