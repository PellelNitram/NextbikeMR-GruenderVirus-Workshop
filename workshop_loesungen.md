# NextbikeMR GruenderVirus Workshop Loesungen

*Martin Lellep*

(c) Martin Lellep 2021; This sample data file belongs to my project "Cycling in Marburg" (http://lellep.xyz/blog/cycling-in-marburg-1-intro.html)*

## Aufgabe 1: Manuelle Begutachtung der Datenlage.

### 1. Was fuer Datentypen sind aufgezeichnet?

Zeitreihen der Zahl der geparkten Nextbikes an verschiedenen Stationen.

### 2. Wieviele Datenpunkte sind enthalten?

Es sind 2381 Datenpunkten mit 6 Kanaelen. Einer der Kanaele enthaelt die Zeitstempel und die restlichen 5 sind Nextbike Stationen.
Es handelt sich um eine kleine Auswahl der gesamten Daten: Dort sind es etwa 600,000 Datenpunkte und 36 Nextbike Stationen.

### 3. Was koennte man damit analysieren?

Eure Kreativitaet ist hier gefragt :-)!

### 4. Was koennte man damit NICHT analysieren?

Eure Kreativitaet ist hier gefragt :-)!

## Aufgabe 2: Analyse des zeitlichen Verlaufs der Zahl der Nextbikes an den verschiedenen Stationen.

Gib den folgenden Code ein:

```python
fig, axes = plt.subplots(1, 2, figsize=(15, 10))
df.plot(ax=axes[0])
df.resample('3h').mean().plot(ax=axes[1])
axes[0].set_title('Raw data')
axes[1].set_title('3h resampled data')
plt.legend()
plt.show()
```

## Aufgabe 3: Zu welchen Zeiten wird besonders viel geparkt?

Gib den folgenden Code ein:

```python
fig, axis = plt.subplots(1, 1, figsize=(10, 10))
df.sum(axis=1).resample('1h').mean().plot.bar(ax=axis, label='Sum of all Nextbike stations')
axis.set_title('Temporal mean: Parked bikes')
plt.legend()
plt.show()
```

## Aufgabe 4: Welche Station ist die groesste Station?

Gib den folgenden Code ein:

```python
fig, axis = plt.subplots(1, 1, figsize=(10, 10))
df.sum(axis=0).plot.bar(ax=axis, label='Sum of all parked bikes per station')
axis.set_title('Largest stations')
plt.legend()
plt.show()
```

## Aufgabe 5: Welche Station ist am haeufigsten leer?

Gib den folgenden Code ein:

```python
fig, axis = plt.subplots(1, 1, figsize=(10, 10))
(df.isin([0]).sum() / df.count() * 100.0).plot.bar(ax=axis, label='Probability to find station empty')
axis.set_title('Empty stations')
plt.legend()
plt.show()
```
