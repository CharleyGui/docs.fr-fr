---
title: Problèmes connus dans SqlClient pour l'Entity Framework
ms.date: 03/30/2017
ms.assetid: 48fe4912-4d0f-46b6-be96-3a42c54780f6
ms.openlocfilehash: 707c749e4dff5d1bbc8d372632aae502092db060
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198104"
---
# <a name="known-issues-in-sqlclient-for-entity-framework"></a>Problèmes connus dans SqlClient pour l'Entity Framework

Cette section décrit les problèmes connus liés au fournisseur de données .NET Framework pour SQL Server (SqlClient).  
  
## <a name="trailing-spaces-in-string-functions"></a>Espaces de fin dans les fonctions de chaîne  

 SQL Server ignore les espaces de fin dans les valeurs de chaîne. Par conséquent, le passage d'espaces de fin dans la chaîne peut provoquer des résultats imprévisibles, voire des défaillances.  
  
 Si votre chaîne doit contenir des espaces de fin, vous devez envisager d’ajouter un espace blanc à la fin, afin que SQL Server ne supprime pas la chaîne. Si les espaces de fin ne sont pas indispensables, ils doivent être supprimés avant le passage au pipeline de la requête.  
  
## <a name="right-function"></a>Fonction RIGHT  

 Si une valeur non `null` est passée comme premier argument et que 0 est passé comme deuxième argument à `RIGHT(nvarchar(max)`, 0`)` ou `RIGHT(varchar(max)`, 0`)`, c’est une valeur `NULL` qui sera retournée, et non une chaîne `empty`.  
  
## <a name="cross-and-outer-apply-operators"></a>Opérateurs CROSS et OUTER APPLY  

 Les opérateurs CROSS et OUTER APPLY ont été introduits dans SQL Server 2005. Dans certains cas, le pipeline de requête peut produire une instruction Transact-SQL qui contient des opérateurs CROSS APPLY et/ou OUTER APPLY. Dans la mesure où certains fournisseurs principaux, y compris les versions de SQL Server antérieures à SQL Server 2005, ne prennent pas en charge ces opérateurs, de telles requêtes ne peuvent pas être exécutées sur ces fournisseurs principaux.  
  
 Vous trouverez ci-dessous quelques scénarios classiques susceptibles d'aboutir à la présence d'opérateurs CROSS APPLY et/ou OUTER APPLY dans la requête de sortie :  
  
- sous-requête corrélée avec pagination ;  
  
- `AnyElement` sur une sous-requête corrélée ou sur une collection produite par navigation ;  
  
- requêtes LINQ qui utilisent des méthodes de regroupement acceptant un sélecteur d'élément ;  
  
- requête dans laquelle un CROSS APPLY ou un OUTER APPLY est explicitement spécifié ;  
  
- requête dotée d'une construction DEREF sur une construction REF.  
  
## <a name="skip-operator"></a>Opérateur SKIP  

 Si vous utilisez SQL Server 2000, l’utilisation de SKIP avec ORDER BY sur des colonnes non-clés peut retourner des résultats incorrects. Le nombre de lignes ignorées peut être supérieur au nombre de lignes spécifié si la colonne non-clé contient des données en double. Cela est dû au fait que SKIP est traduit pour SQL Server 2000. Par exemple, dans la requête suivante, plus de cinq lignes peuvent être ignorées si `E.NonKeyColumn` contient des valeurs en double :  
  
```sql  
SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L  
```  
  
## <a name="targeting-the-correct-sql-server-version"></a>Ciblage de la version appropriée de SQL Server  

 Le Entity Framework cible la requête Transact-SQL en fonction de la version de SQL Server spécifiée dans l' `ProviderManifestToken` attribut de l’élément Schema dans le fichier de modèle de stockage (. SSDL). Cette version de SQL Server peut ne pas correspondre à celle à laquelle vous êtes connecté. Par exemple, si vous utilisez SQL Server 2005, mais que votre `ProviderManifestToken` attribut a la valeur 2008, la requête Transact-SQL générée peut ne pas s’exécuter sur le serveur. Par exemple, une requête qui utilise les nouveaux types date/heure introduits dans SQL Server 2008 ne s'exécutera pas sur les versions antérieures de SQL Server. Si vous utilisez SQL Server 2005, mais que votre `ProviderManifestToken` attribut a la valeur 2000, la requête Transact-SQL générée peut être moins optimisée, ou vous pouvez obtenir une exception qui indique que la requête n’est pas prise en charge. Pour plus d'informations, voir la section Opérateurs CROSS et OUTER APPLY, plus haut dans cette rubrique.  
  
 Certains comportements de base de données dépendent du niveau de compatibilité défini pour la base de données. Si votre `ProviderManifestToken` attribut est défini sur 2005 et que votre version de SQL Server est 2005, mais que le niveau de compatibilité d’une base de données est défini sur « 80 » (SQL Server 2000), le Transact-SQL généré ciblera SQL Server 2005, mais peut ne pas s’exécuter comme prévu en raison du paramètre de niveau de compatibilité. Par exemple, vous pouvez perdre des informations de classement si un nom de colonne dans la liste ORDER BY correspond à un nom de colonne dans le sélecteur.  
  
## <a name="nested-queries-in-projection"></a>Requêtes imbriquées dans la projection  

 Les requêtes imbriquées d'une clause de projection peuvent être traduites en requêtes de produit cartésien sur le serveur. Sur certains serveurs principaux, y compris les SQL Server, la table TempDB peut devenir très volumineuse. et une diminution des performances du serveur.  
  
 Vous trouverez ci-dessous un exemple de requête imbriquée dans une clause de projection :  
  
```sql  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="server-generated-guid-identity-values"></a>Valeurs d'identité GUID générées par le serveur  

 Le Entity Framework prend en charge les valeurs d’identité de type GUID générées par le serveur, mais le fournisseur doit prendre en charge le retour de la valeur d’identité générée par le serveur après l’insertion d’une ligne. À compter de SQL Server 2005, vous pouvez retourner le type GUID généré par le serveur dans une base de données SQL Server à l’aide de la [clause OUTPUT](/sql/t-sql/queries/output-clause-transact-sql).
  
## <a name="see-also"></a>Voir aussi

- [SqlClient pour Entity Framework](sqlclient-for-the-entity-framework.md)
- [Problèmes connus et éléments à prendre en compte dans LINQ to Entities](./language-reference/known-issues-and-considerations-in-linq-to-entities.md)
