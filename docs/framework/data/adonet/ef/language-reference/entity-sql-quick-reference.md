---
title: Aide-mémoire Entity SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 9ccfc461d394af8804c960ebf460e7fbfb025b64
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833873"
---
# <a name="entity-sql-quick-reference"></a>Aide-mémoire Entity SQL
Cette rubrique fournit un aide-mémoire sur les requêtes [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Les requêtes de cette rubrique sont basées sur le modèle de vente AdventureWorks Sales Model.  
  
## <a name="literals"></a>Littéraux  
  
### <a name="string"></a>String  
 Les chaînes de caractères littérales peuvent être au format Unicode ou non-Unicode. Les chaînes Unicode sont précédées de N. Par exemple, `N'hello'`.  
  
 Exemple de littéral de chaîne non-Unicode :  
  
```sql  
'hello'  
--same as  
"hello"  
```  
  
 Sortie :  
  
|`Value`|  
|-----------|  
|hello|  
  
### <a name="datetime"></a>DateTime  
 Dans les littéraux DateTime, les parties date et heure sont obligatoires. Il n'existe pas de valeur par défaut.  
  
 Exemple :  
  
```sql  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 Sortie :  
  
|Valeur|  
|-----------|  
|12/25/2006 1:01:00 AM|  
  
### <a name="integer"></a>Entier  
 Les littéraux d'entiers peuvent être de type Int32 (123), UInt32 (123U), Int64 (123L) et UInt64 (123UL).  
  
 Exemple :  
  
```sql  
--a collection of integers  
{1, 2, 3}  
```  
  
 Sortie :  
  
|Valeur|  
|-----------|  
|1|  
|2|  
|3|  
  
### <a name="other"></a>Autre  
 Les autres littéraux pris en charge par [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont Guid, Binary, Float/Double, Decimal et la valeur `null`. Les littéraux NULL dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont considérés compatibles avec tous les autres types dans le modèle conceptuel.  
  
## <a name="type-constructors"></a>Constructeurs de type  
  
### <a name="row"></a>ROW  
 La [ligne](row-entity-sql.md) construit une valeur anonyme, structurellement typée (enregistrement) comme dans : `ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 Exemple :  
  
```sql  
SELECT VALUE row (product.ProductID AS ProductID, product.Name
    AS ProductName) FROM AdventureWorksEntities.Product AS product
```  
  
 Sortie :  
  
|ProductID|Nom|  
|---------------|----------|  
|1|Adjustable Race|  
|879|All-Purpose Bike Stand|  
|712|AWC Logo Cap|  
|...|...|  
  
### <a name="multiset"></a>MULTISET  
 Les collections de [multiensembles](multiset-entity-sql.md), telles que :  
  
 `MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`  
  
 Exemple :  
  
```sql  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 Sortie :  
  
|ProductID|Nom|ProductNumber|…|  
|---------------|----------|-------------------|-------|  
|842|Touring-Panniers, Large|PA-T100|…|  
  
### <a name="object"></a>Object  
 Le [constructeur de type nommé](named-type-constructor-entity-sql.md) construit (nommé) des objets définis par l’utilisateur, tels que `person("abc", 12)`.  
  
 Exemple :  
  
```sql  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 Sortie :  
  
|SalesOrderDetailID|CarrierTrackingNumber|OrderQty|ProductID|...|  
|------------------------|---------------------------|--------------|---------------|---------|  
|1|4911-403C-98|1|776|...|  
|2|4911-403C-98|3|777|...|  
|...|...|...|...|...|  
  
## <a name="references"></a>Références  
  
### <a name="ref"></a>REF  
 [Ref](ref-entity-sql.md) crée une référence à une instance de type d’entité. Par exemple, la requête suivante retourne les références à chaque entité Order dans le jeu d'entités Orders :  
  
```sql  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 Sortie :  
  
|Valeur|  
|-----------|  
|1|  
|2|  
|3|  
|...|  
  
 L'exemple suivant utilise l'opérateur d'extraction de propriété (.) pour accéder à une propriété d'entité. Lors de l'utilisation de l'opérateur d'extraction de propriété, la référence est automatiquement supprimée.  
  
 Exemple :  
  
```sql  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product AS p
```  
  
 Sortie :  
  
|`Value`|  
|-----------|  
|Adjustable Race|  
|All-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### <a name="deref"></a>DEREF  
 [Deref](deref-entity-sql.md) déréférence une valeur de référence et génère le résultat de ce déréférencement. Par exemple, la requête suivante génère les entités Order pour chaque élément Order du jeu d'entités Orders : `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`.  
  
 Exemple :  
  
```sql  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product AS p
```  
  
 Sortie :  
  
|`Value`|  
|-----------|  
|Adjustable Race|  
|All-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### <a name="createref-and-key"></a>CREATEREF et KEY  
 [CREATEREF](createref-entity-sql.md) crée une référence qui transmet une clé. La [clé](key-entity-sql.md) extrait la partie clé d’une expression avec une référence de type.  
  
 Exemple :  
  
```sql  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product AS p
```  
  
 Sortie :  
  
|ProductID|  
|---------------|  
|980|  
|365|  
|771|  
|...|  
  
## <a name="functions"></a>Fonctions  
  
### <a name="canonical"></a>Canonical  
 L’espace de noms des [fonctions canoniques](canonical-functions.md) est EDM, comme dans `Edm.Length("string")`. Vous n'avez pas besoin de spécifier l'espace de noms sauf si un autre espace de noms est importé et qu'il contient une fonction portant le même nom qu'une fonction canonique. Si deux espaces de noms partagent la même fonction, l'utilisateur doit spécifier le nom complet.  
  
 Exemple :  
  
```sql  
SELECT Length(c. FirstName) AS NameLen FROM
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 Sortie :  
  
|NameLen|  
|-------------|  
|6\.|  
|6\.|  
|5\.|  
  
### <a name="microsoft-provider-specific"></a>Spécifiques au fournisseur Microsoft  
 Les [fonctions spécifiques au fournisseur Microsoft](../sqlclient-for-ef-functions.md) se trouvent dans l’espace de noms `SqlServer`.  
  
 Exemple :  
  
```sql  
SELECT SqlServer.LEN(c.EmailAddress) AS EmailLen FROM
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 Sortie :  
  
|EmailLen|  
|--------------|  
|27|  
|27|  
|26|  
  
## <a name="namespaces"></a>Espaces de noms  
 [L’utilisation](using-entity-sql.md) de spécifie les espaces de noms utilisés dans une expression de requête.  
  
 Exemple :  
  
```sql  
using SqlServer; LOWER('AA');  
```  
  
 Sortie :  
  
|`Value`|  
|-----------|  
|aa|  
  
## <a name="paging"></a>Pagination  
 La pagination peut être exprimée en déclarant une sous-clause [Skip](skip-entity-sql.md) et [Limit](limit-entity-sql.md) à la clause [order by](order-by-entity-sql.md) .  
  
 Exemple :  
  
```sql  
SELECT c.ContactID as ID, c.LastName AS Name FROM
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 Sortie :  
  
|ID|Nom|  
|--------|----------|  
|10|Adina|  
|11|Agcaoili|  
|12|Aguilar|  
  
## <a name="grouping"></a>Regroupement  
 [Regroupement par](group-by-entity-sql.md) spécifie les groupes dans lesquels les objets retournés par une expression de requête ([Select](select-entity-sql.md)) doivent être placés.  
  
 Exemple :  
  
```sql  
SELECT VALUE name FROM AdventureWorksEntities.Product AS P
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 Sortie :  
  
|name|  
|----------|  
|LL Mountain Seat Assembly|  
|ML Mountain Seat Assembly|  
|HL Mountain Seat Assembly|  
|...|  
  
## <a name="navigation"></a>Navigation  
 L'opérateur de navigation de relations vous permet de parcourir la relation entre une entité (terminaison From) et une autre entité (terminaison To). [Naviguer](navigate-entity-sql.md) prend le type de relation qualifié comme \<namespace >. \<relationship nom de type >. Navigate retourne\<Ref T > si la cardinalité de la terminaison to est 1. Si la cardinalité de la terminaison to est n, la collection < Ref\<T > > sera retourné.  
  
 Exemple :  
  
```sql  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 Sortie :  
  
|AddressID|  
|---------------|  
|1|  
|2|  
|3|  
|...|  
  
## <a name="select-value-and-select"></a>SELECT VALUE et SELECT  
  
### <a name="select-value"></a>SELECT VALUE  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fournit la clause SELECT VALUE pour ignorer la construction de ligne implicite. Un seul élément peut être spécifié dans une clause SELECT VALUE. Lorsqu’une telle clause est utilisée, aucun Wrapper de ligne n’est construit autour des éléments de la clause SELECT, et une collection de la forme souhaitée peut être produite, par `SELECT VALUE a`exemple :.  
  
 Exemple :  
  
```sql  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product AS p
```  
  
 Sortie :  
  
|Nom|  
|----------|  
|Adjustable Race|  
|All-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### <a name="select"></a>SELECT  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fournit également le constructeur de ligne pour construire des lignes arbitraires. SELECT extrait un ou plusieurs éléments de la projection et produit un enregistrement de données avec des champs, par exemple : `SELECT a, b, c`.  
  
 Exemple :  
  
 SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:  
  
|Name|ProductID|  
|----------|---------------|  
|Adjustable Race|1|  
|All-Purpose Bike Stand|879|  
|AWC Logo Cap|712|  
|...|...|  
  
## <a name="case-expression"></a>Expression CASE  
 L' [expression case](case-entity-sql.md) évalue un jeu d’expressions booléennes pour déterminer le résultat.  
  
 Exemple :  
  
```sql  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 Sortie :  
  
|`Value`|  
|-----------|  
|TRUE|  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
- [Vue d’ensemble d’Entity SQL](entity-sql-overview.md)
