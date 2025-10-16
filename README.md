# TP-Pandas-DataFrame-tp3
import pandas as pd

#######Charger le fichier
data= """Produit,Catégorie,Vendeur,Quantité,Prix_Unitaire,Ville
Laptop,Électronique,Ali,3,7500,Fès
Casque,Électronique,Sara,5,400,Rabat
Tablette,Électronique,Omar,2,3500,Fès
Chemise,Vêtements,Laila,7,250,Tanger
Pantalon,Vêtements,Youssef,4,300,Marrakech
Livre,Livres,Hassan,10,120,Rabat
Crème,Beauté,Sara,6,90,Fès
Parfum,Beauté,Laila,3,400,Marrakech
Jeans,Vêtements,Omar,5,350,Tanger
Stylo,Livres,Ali,12,25,Fès"""

with open("data.csv", "w", encoding="utf-8") as f:
    f.write(data)

df=pd.read_csv("data.csv")
print(df)

print(df.head(5))

#######Découverte du DataFrame

print("#####################################################")
#Afficher le nombre total de lignes et de colonnes.
print(df.shape)

print("#####################################################")
#Vérifier le type de données de chaque colonne
print(df.dtypes)

print("#####################################################")
#Afficher les valeurs uniques de la colonne “Ville”
print(df["Ville"].unique())

print("#####################################################")
#Afficher les informations générales sur le DataFrame
print(df.info())

#########Opérations de base

print("#####################################################")
#Ajouter une colonne Total = Quantité × Prix_Unitaire.
df["Total"] = df["Quantité"] * df["Prix_Unitaire"]
print(df)

print("#####################################################")
#Trier les ventes selon le montant total (du plus grand au plus petit)
df_trie = df.sort_values(by="Total", ascending=False)
print(df_trie)

print("#####################################################")
#Afficher uniquement les lignes où la catégorie est “Électronique”
df_electronique = df[df["Catégorie"] == "Électronique"]
print(df_electronique)

################Analyse statistique

print("#####################################################")
#Somme totale des ventes
somme_ventes = df["Total"].sum()
print(somme_ventes)

print("#####################################################")
#Moyenne du prix unitaire
moyenne_prix = df["Prix_Unitaire"].mean()
print(moyenne_prix)

print("#####################################################")
#Produit le plus vendu (en quantité)
produit_max = df.loc[df["Quantité"].idxmax(), "Produit"]
quantite_max = df["Quantité"].max()
print(produit_max)

print("#####################################################")
#Prix unitaire maximum et minimum
prix_max = df["Prix_Unitaire"].max()
prix_min = df["Prix_Unitaire"].min()
print(prix_max)
print(prix_min)
