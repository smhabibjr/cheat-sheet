1.1 Name , Vorname, Gehalt, Prämie aller Mitarbeiter
````
SELECT
	name,
	vorname,
	gehalt,
	bonus
FROM Firma.dbo.mitarbeiter M
ORDER BY name, vorname ASC;
````

1.2 Name, Vorname, Gehalt, Prämie, Verdienst = Summe (Gehalt + Prämie) aller 	Mitarbeiter
````
SELECT
	Name,
	vorname,
	gehalt,
	bonus,
	verdienst = ISNULL(gehalt, 0) + ISNULL(bonus, 0)
FROM Firma.dbo.mitarbeiter M
ORDER BY name, vorname ASC;
````

1.3 Durchschnittseinkommen (Gehalt + Prämie) aller Mitarbeiter
````
SELECT
	durchschnitt = AVG(ISNULL(gehalt, 0) + ISNULL(bonus, 0))
FROM Firma.dbo.mitarbeiter;
````

1.4 Name, Vorname der Mitarbeiter, die keine Prämie bekommen
````
SELECT
	name,
	vorname
FROM Firma.dbo.mitarbeiter M
WHERE bonus IS NULL
ORDER BY name, vorname ASC;
````

1.5 Name, Vorname der Mitarbeiter der Abteilung 2
````
SELECT
	name,
	vorname
FROM Firma.dbo.mitarbeiter M
WHERE M.abteilungen_id = 2
ORDER BY name, vorname ASC;
````

1.6 Durchschnittsalter aller Mitarbeiter in Jahren
````
SELECT
	durchschnittsalter = AVG(DATEDIFF(YEAR, M.gebdatum, GETDATE()))
FROM Firma.dbo.mitarbeiter M;
````

1.7 Name, Vorname der Mitarbeiter, deren Familienname auf „er“ endet
````
SELECT
	name,
	vorname
FROM Firma.dbo.mitarbeiter M
WHERE RIGHT(name, 2) = 'er';
````

1.8 Name, Vorname der Mitarbeiter, deren Familienname als 2. Buchstabe ein „e“ hat
````
SELECT
	name,
	vorname
FROM Firma.dbo.mitarbeiter M
WHERE SUBSTRING(name, 2, 1) = 'e';
````

1.9 Name, Vorname der Mitarbeiter, die keinen Eintrag „Chef“ haben oder die ihr 	eigener Chef sind.
````
SELECT
	name,
	vorname
FROM Firma.dbo.mitarbeiter M
WHERE chef_id IS NULL
OR CHEF_id = id
ORDER BY name, vorname ASC;
````

2.1 Monatsnamen und die Anzahl der Mitarbeiter, die im jeweiligen Monat Geburtstag 	haben, nach der Anzahl absteigend sortiert.
````
SELECT
	monat = DATENAME(MONTH, gebdatum),
	anzahl = COUNT(id)
FROM Firma.dbo.mitarbeiter M
GROUP BY DATENAME(MONTH, gebdatum)
ORDER BY anzahl DESC;
````

2.2 Zeigen Sie alle Leiter an (MID genügt) und die Anzahl der ihnen direkt 	unterstellten Mitarbeiter.
````
SELECT
	chef_id,
	anzahl = COUNT(M.id)
FROM Firma.dbo.abteilungen A
INNER JOIN Firma.dbo.mitarbeiter M
ON M.abteilungen_id = A.id
WHERE chef_id IS NOT NULL
GROUP BY chef_id
ORDER BY chef_id ASC;
````

3.1 Name, Vorname der Mitarbeiter, Name der Abteilung
````
SELECT
	M.name,
	M.vorname,
	A.name
FROM Firma.dbo.mitarbeiter M
INNER JOIN Firma.dbo.abteilungen A
ON A.id = M.abteilungen_id
ORDER BY A.name ASC;
````

3.2 AID, Name der Abteilung und Durchschnittsgehalt, sofern nicht NULL
````
SELECT
	A.id,
	bezeichnung = MIN(A.[name]),
	gehalt = AVG(ISNULL(gehalt, 0))
FROM Firma.dbo.abteilungen A
INNER JOIN Firma.dbo.mitarbeiter M
ON M.abteilungen_id = A.id
GROUP BY A.id
ORDER BY gehalt DESC;
````

3.3 AID, Abteilungsname und Anzahl der Mitarbeiter für jede Abteilung
````
SELECT
	A.id,
	bezeichnung = MIN(A.[name]),
	anzahl = COUNT(M.id)
FROM Firma.dbo.abteilungen A
LEFT JOIN Firma.dbo.mitarbeiter M
ON M.abteilungen_id = A.id
GROUP BY A.id;
````

-- 3.4 AID, Abteilungsname, Summe der Grundgehälter pro Abteilung, sortiert nach AID
````
SELECT
	A.id,
	bezeichnung = MIN(A.[name]),
	gehalt = SUM(ISNULL(gehalt, 0))
FROM Firma.dbo.abteilungen A
INNER JOIN Firma.dbo.mitarbeiter M
ON M.abteilungen_id = A.id
GROUP BY A.id
ORDER BY A.id ASC;
````

3.5 AID, Abteilungsname, Durchschnittseinkommen (Gehalt + Prämie) pro Abteilung,
	sortiert nach Einkommen, das größte Einkommen zuerst.

````
SELECT
	A.id,
	bezeichnung = MIN(A.[name]),
	gehalt = AVG(ISNULL(gehalt, 0) + ISNULL(bonus, 0))
FROM Firma.dbo.abteilungen A
INNER JOIN Firma.dbo.mitarbeiter M
ON M.abteilungen_id = A.id
GROUP BY A.id
ORDER BY gehalt DESC;
````

4.1 Setzen Sie das Gehalt von Mitarbeiter Nr. 101 auf 7000 Euro.
````
UPDATE Firma.dbo.mitarbeiter SET
	gehalt = 7000
WHERE id = 101;
````

4.2 Wer weniger als 2000 Euro hat, erhält eine Gehaltserhöhung von 10%
````
UPDATE Firma.dbo.mitarbeiter SET
	gehalt = gehalt * 1.1
WHERE gehalt < 2000;
````

5.1 Zeigen Sie alle Leiter an (MID, Name) und die Anzahl der ihnen direkt 	unterstellten Mitarbeiter, absteigend nach der Anzahl sortiert
````
SELECT
	C.id,
	name = C.name,
	anzahl = COUNT(M.id)
FROM Firma.dbo.mitarbeiter C
INNER JOIN Firma.dbo.mitarbeiter M
ON M.chef_id = C.id
GROUP BY C.id, C.name
ORDER BY anzahl DESC;
````

5.2 Wie 5.1 aber sortiert alphabetisch nach Namen des Vorgesetzten
````
SELECT
	C.id,
	name = C.name,
	anzahl = COUNT(M.id)
FROM Firma.dbo.mitarbeiter C
INNER JOIN Firma.dbo.mitarbeiter M
ON M.chef_id = C.id
GROUP BY C.id, C.name
ORDER BY name ASC;
````

5.3 Wie 5.1 aber nur die Leiter mit mindestens 4 Mitarbeitern.
````
SELECT
	C.id,
	C.name,
	S.anzahl
FROM (
	SELECT
		C.id,
		anzahl = COUNT(M.id)
	FROM Firma.dbo.mitarbeiter C
	INNER JOIN Firma.dbo.mitarbeiter M
	ON M.chef_id = C.id
	GROUP BY C.id
) S
INNER JOIN Firma.dbo.mitarbeiter C
ON C.id = S.id
WHERE anzahl >= 4
ORDER BY anzahl DESC;
````

5.4 Wie 5.1 und zusätzlich den Namen der Abteilung
````
SELECT
	M.id,
	M.name,
	S.anzahl,
	A.name
FROM (
	SELECT
		C.id,
		anzahl = COUNT(M.id)
	FROM Firma.dbo.mitarbeiter C
	INNER JOIN Firma.dbo.mitarbeiter M
	ON M.chef_id = C.id
	GROUP BY C.id
) S
INNER JOIN Firma.dbo.mitarbeiter M
ON M.id = S.id
INNER JOIN Firma.dbo.abteilungen A
ON A.id = M.abteilungen_id
ORDER BY anzahl DESC;
````
5.5 Name, Vorname , Geburtsdatum des ältesten Mitarbeiters
````
SELECT
	M.name,
	M.vorname,
	S.gebdatum
FROM Firma.dbo.mitarbeiter M
INNER JOIN (
	SELECT
		gebdatum = MIN(gebdatum)
	FROM Firma.dbo.mitarbeiter
	) S
ON M.gebdatum = S.gebdatum;

SELECT TOP 1
	name,
	vorname,
	gebdatum
FROM Firma.dbo.mitarbeiter
ORDER BY gebdatum ASC;
````

-- 5.6 Liste der Mitarbeiter (nur Name, Vorname) mit dem Namen des direkten 	jeweiligen Vorgesetzten sofern vorhanden, sortiert nach dem Alter der Mitarbeiter 	[dem Namen des Vorgesetzten].
````
SELECT
	Name = M.name,
	Vorname = M.vorname,
	Chef = C.name
FROM Firma.dbo.mitarbeiter M
LEFT JOIN Firma.dbo.mitarbeiter C
ON C.id = M.chef_id
ORDER BY M.gebdatum ASC;
````

-- 5.7 Liste aller Mitarbeiter (ID, Name, Vorname), die keine Untergebenen haben.
````
SELECT
	S.id,
	C.name,
	C.vorname,
	S.Anzahl
FROM (
	SELECT
		C.id,
		Anzahl = COUNT(M.id)
	FROM Firma.dbo.mitarbeiter C
	LEFT JOIN Firma.dbo.mitarbeiter M
	ON M.chef_id = C.id
	GROUP BY C.id
) S
INNER JOIN Firma.dbo.mitarbeiter C
ON C.id = S.id
WHERE S.Anzahl = 0;
````
5.8 Anzahl aller Mitarbeiter mit Gehalt unter 3000 EUR, 3000-3999 EUR, 
	4000-4999 EUR und darüber.

````
SELECT
	[<3000] = S1.anzahl,
	[3000-3999] = S2.anzahl,
	[4000-4999] = S3.anzahl,
	[>=5000] = S4.anzahl
FROM (
	SELECT
		anzahl = COUNT(M.id)
	FROM Firma.dbo.mitarbeiter M
	WHERE M.gehalt < 3000
	) S1,
	(
	SELECT
		anzahl = COUNT(M.id)
	FROM Firma.dbo.mitarbeiter M
	WHERE M.gehalt BETWEEN 3000 AND 3999
	) S2,
	(
	SELECT
		anzahl = COUNT(M.id)
	FROM Firma.dbo.mitarbeiter M
	WHERE M.gehalt BETWEEN 4000 AND 4999
	) S3,
	(
	SELECT
		anzahl = COUNT(M.id)
	FROM Firma.dbo.mitarbeiter M
	WHERE M.gehalt > 5000
	) S4
;
````

-- 6.1
-- �bersprungen

-- 6.2 Zeigen Sie alle KID, Namen und Vornamen der Kunden mit dem Namen des 	betreuenden Mitarbeiters an. Sortieren Sie nach MID.
````
SELECT
	KID = K.ID,
	K.Name,
	K.Vorname,
	M.name
FROM Firma.dbo.kunde K
INNER JOIN Firma.dbo.mitarbeiter M
ON M.id = K.Mitarbeiter_ID
ORDER BY M.id ASC;
````

-- 6.3 Zeigen Sie alle Mitarbeiter an und die Anzahl der von Ihnen betreuten Kunden.
````
SELECT
	M.name,
	M.vorname,
	anzahl = ISNULL(S.anzahl, 0)
FROM Firma.dbo.mitarbeiter M
LEFT JOIN (
	SELECT
		id = M.id,
		anzahl = COUNT(K.id)
	FROM Firma.dbo.mitarbeiter M
	INNER JOIN Firma.dbo.kunde K
	ON K.Mitarbeiter_ID = M.id
	GROUP BY M.id
	) S
ON S.id = M.id
ORDER BY anzahl DESC;

````
-- 6.4 Wie 6.3 und zusätzlich die Anzahl der betreuten Kunden für jede Abteilung sofern 	vorhanden, nach dem Namen der Abteilungen geordnet.
````
SELECT
	A.name,
	M.name,
	M.vorname,
	anzahl = ISNULL(S.anzahl, 0)
FROM Firma.dbo.abteilungen A
LEFT JOIN Firma.dbo.mitarbeiter M
ON A.id = M.abteilungen_id
LEFT JOIN (
	SELECT		-- Mitarbeiter / Anzahl Kunden
		id = M.id,
		anzahl = COUNT(K.id)
	FROM Firma.dbo.mitarbeiter M
	LEFT JOIN Firma.dbo.kunde K
	ON K.Mitarbeiter_ID = M.id
	GROUP BY M.id
	) S
ON S.id = M.id
WHERE anzahl > 0
UNION
SELECT			-- Abteilung / Anzahl Kunden und Abteilungen ohne Mitarbeiter
	A.name,
	NULL,
	NULL,
	anzahl = ISNULL(S.anzahl, 0)
FROM Firma.dbo.abteilungen A
LEFT JOIN Firma.dbo.mitarbeiter M
ON A.id = M.abteilungen_id
LEFT JOIN (
	SELECT		-- Abteilung / Anzahl Kunden
		id = A.id,
		anzahl = COUNT(K.id)
	FROM Firma.dbo.abteilungen A
	LEFT JOIN Firma.dbo.mitarbeiter M
	ON M.abteilungen_id = A.id
	LEFT JOIN Firma.dbo.kunde K
	ON K.Mitarbeiter_ID = M.id
	GROUP BY A.id
	) S
ON S.id = A.id
ORDER BY A.name ASC;
````

-- 6.5 Zeigen Sie Kunden an, die miteinander verwandt sein könnten, weil sie den 	gleichen Familiennamen haben.
````
SELECT
	K1.ID,
	K1.name,
	K1.vorname
FROM Firma.dbo.kunde K1
INNER JOIN Firma.dbo.kunde K2
ON K1.Name = K2.Name
AND K1.ID <> K2.ID
ORDER BY K1.name, K1.Vorname ASC;
````

-- 7.1 Welche Mitarbeiter verdienen mehr als der Durchschnitt aller Mitarbeiter?
````
SELECT
	M1.vorname,
	M1.name,
	M1.gehalt
FROM Firma.dbo.mitarbeiter M1
INNER JOIN(
	SELECT
		Schnitt = AVG(M2.gehalt)
	FROM Firma.dbo.mitarbeiter M2
	) S
ON M1.gehalt > S.schnitt
````

-- 7.2 Zeigen Sie zusätzlich zu 7.1 noch eine Spalte an, die immer den 	Durchschnittsverdienst aller anzeigt.
````
SELECT
	M1.vorname,
	M1.name,
	M1.gehalt,
	S.schnitt
FROM Firma.dbo.mitarbeiter M1
INNER JOIN(
	SELECT
		Schnitt = AVG(M2.gehalt)
	FROM Firma.dbo.mitarbeiter M2
	) S
ON M1.gehalt > S.schnitt
ORDER BY M1.gehalt DESC
````

-- 7.3  Welche Mitarbeiter verdienen weniger als der Durchschnitt ihrer Abteilung?
````
SELECT
	M1.vorname,
	M1.name,
	M1.gehalt
FROM Firma.dbo.mitarbeiter M1
INNER JOIN(
	SELECT
		M2.abteilungen_id,
		Schnitt = AVG(M2.gehalt)
	FROM Firma.dbo.mitarbeiter M2
	GROUP BY M2.abteilungen_id
	) S
ON M1.abteilungen_id = S.abteilungen_id
AND M1.gehalt < S.schnitt
INNER JOIN Firma.dbo.abteilungen A
ON A.id = M1.abteilungen_id
ORDER BY A.id, M1.name
````

-- 7.4 Zeigen Sie zusätzlich zu 7.3 noch je eine Spalte an, die immer den 	Durchschnittsverdienst der jeweiligen Abteilung und den Namen der Abteilung 	enthält. Ordnen Sie nach Verdienst innerhalb der Abteilung.
````

SELECT
	M1.vorname,
	M1.name,
	M1.gehalt,
	Abteilung = A.name,
	S.schnitt
FROM Firma.dbo.mitarbeiter M1
INNER JOIN(
	SELECT
		M2.abteilungen_id,
		Schnitt = AVG(M2.gehalt)
	FROM Firma.dbo.mitarbeiter M2
	GROUP BY M2.abteilungen_id
	) S
ON M1.abteilungen_id = S.abteilungen_id
AND M1.gehalt < S.schnitt
INNER JOIN Firma.dbo.abteilungen A
ON A.id = M1.abteilungen_id
ORDER BY A.id, M1.name
````

7.5 Zeigen Sie incl. des Durchschnittsverdienstes alle diejenigen Mitarbeiter und den 	Abteilungsnamen an, deren Verdienst sich um höchstens 500 EUR vom 	Durchschnitt der jeweiligen Abteilung unterscheidet.
````
SELECT
	M1.vorname,
	M1.name,
	M1.gehalt,
	Abteilung = A.name,
	S.schnitt
FROM Firma.dbo.mitarbeiter M1
INNER JOIN(
	SELECT
		M2.abteilungen_id,
		Schnitt = AVG(M2.gehalt)
	FROM Firma.dbo.mitarbeiter M2
	GROUP BY M2.abteilungen_id
	) S
ON M1.abteilungen_id = S.abteilungen_id
AND ABS(M1.gehalt - S.Schnitt) <= 500 --M1.gehalt < S.schnitt
INNER JOIN Firma.dbo.abteilungen A
ON A.id = M1.abteilungen_id
ORDER BY A.id, M1.name
````

7.6 Alle Monate ohne Geburtstage in der Firma.
````
SELECT
	S.Monat
FROM(
	SELECT DISTINCT
		Monat = DATEPART(MONTH, M.gebdatum)
	FROM Firma.dbo.mitarbeiter M
	) S


INNER JOIN (1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12)
````
