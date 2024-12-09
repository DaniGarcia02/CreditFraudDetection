# CreditFraudDetection

## Introducció
L'Objectiu d'aquest projecte es trobar un model que obtingui la màxima F1-score possible per a detecció d'opreacions bancaries fraudulentes.

## Dataset
[Credit Card Fraud Detection](https://www.kaggle.com/mlg-ulb/creditcardfraud)

Aquest dataset conté transaccions bancaries fetes al Septembre de 2013 per diversos usuaris de tragetes bancaries Europeus.
El dataset conté les transaccions que van ocurrir durant 2 dies on 492 van ser fraudulentes de 284807 en total.

Les entrades del dataset només contenen dades numèriques que son el resultat d'aplicar la transformació PCA, degut a temes de confidiencialitat no es pot saber clarament que representa cada columna o valor.
Les úniques columnes sense ser transformada son 'Time', 'Amount' i 'Class'. La Feature 'Time' respresenta el temps que ha passat des de la primera entrada del dataset, la feature 'Amount' representa la quantitat de diners de la transacció i la Feature 'Class' ens diu si aquesta transacció es fraudulenta o no.

## Exploració de les dades

