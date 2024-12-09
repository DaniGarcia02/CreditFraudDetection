# CreditFraudDetection

## Introducció
L'Objectiu d'aquest projecte es trobar un model que obtingui la màxima F1-score possible per a la detecció d'operacions bancàries fraudulentes

## Dataset
[Credit Card Fraud Detection](https://www.kaggle.com/mlg-ulb/creditcardfraud)

Aquest dataset conté transaccions bancaries fetes al Septembre de 2013 per diversos usuaris de tragetes bancaries Europeus.
El dataset conté les transaccions que van ocurrir durant 2 dies on 492 van ser fraudulentes de 284807 en total.

Les entrades del dataset només contenen dades numèriques que son el resultat d'aplicar la transformació PCA, degut a temes de confidiencialitat no es pot saber clarament que representa cada columna o valor.
Les úniques columnes sense ser transformada son 'Time', 'Amount' i 'Class'. La Feature 'Time' respresenta el temps que ha passat des de la primera entrada del dataset, la feature 'Amount' representa la quantitat de diners de la transacció i la Feature 'Class' ens diu si aquesta transacció es fraudulenta o no.

## Metodologia
### Mètrica
Degut al gran imbalanceig de dades que n'hi ha la mètrica que utilitzaré serà F1-Score, això es degut a que en un cas amb dades imbaalancejades com aquest el que volem minimitzar son els casos False Positive i False Negative. En aquestcas concret una predicció False Positive provocaria que la targeta de crèdit d'un client es bloquejés sense que aquest hagi comés una infracció, en canvi, una predicció False Negative significa que hi ha hagut una transacció fraudulenta que no hem identificat. Ambdós casos son dolents per això volem utilitzar F1-Score en comptes de només precision o recall.

### Tractament de l'imbalanceig de dades
Per tractar amb l'imbalanceig de dades utilitzo dues tècniques:
- Undersampling: Consisteix en reduir les dades de la classe majoritària per que la seva proporció sigui igual o més propera a la calsse minoritària, l'inconvenitent que té es que eleminany es poden perdre relacions importants per a la predicció i obtindre resultats dolents.
- Oversampling: Es el contrari que Undersampling, augmentem les dades de la classe minoritària fins que tingui una proporció igual o semblant a la de la classe majoritària. En aquest cas els inconvenients que tenen es que al fer Cross-Validation s'ha d'aplicar aquest mètode per a cada partició individualment. ja que sinò es produiria 'Data Leakage' al haber afegit dades basades en el dataset complet al set de Validació.

### Models
He pobat diferents models per poder comparar els seus resultats, els models utilitzats han sigut:
- Linear Regression.
- K Nearest Neighbours.
- Linear SVM.
- Decision Tree.
- Random Forest.
- XGBoost.

Finalment degut tant als seus resultats i al temps d'execució el millor model ha sigut XGBoost.

### Cerca d'hiperparàmetres
Per la cerca d'hiperparàmetres sense aplicar overfitting he utilitzat la funció GridSearch de sklearn, aplicant Oversampling he utilitzat Cross-Validation pper comprobar el resultat de diferents parametres i escullir els millors

## Resultats
Els resultats obtinguts amb XGBoost han sigut els següents:

Sense Oversampling
<br>
  <img src ="https://github.com/DaniGarcia02/CreditFraudDetection/blob/main/img/pr_curve_best.png">
<br>

Amb Oversampling
<br>
  <img src ="https://github.com/DaniGarcia02/CreditFraudDetection/blob/main/img/pr_curve_oversampling.png">
<br>

