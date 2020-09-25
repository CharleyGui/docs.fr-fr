---
title: Dépannage
ms.date: 03/30/2017
ms.assetid: 8cd4401c-b12c-4116-a421-f3dcffa65670
ms.openlocfilehash: 0ac71d9a55e92161f24deb490b8df6148bfc840c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202186"
---
# <a name="troubleshooting"></a>Résolution des problèmes

Les informations suivantes exposent quelques problèmes que vous pouvez rencontrer dans vos applications [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] et fournissent des suggestions pour les éviter, ou du moins en réduire l'effet.  
  
 D’autres problèmes sont traités dans le [Forum aux questions](frequently-asked-questions.md).  
  
## <a name="unsupported-standard-query-operators"></a>Opérateurs de requête standard non pris en charge  

 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ne prend pas en charge toutes les méthodes d'opérateur de requête standard (par exemple, <xref:System.Linq.Enumerable.ElementAt%2A>). En conséquence, les projets qui sont compilés peuvent produire des erreurs d'exécution. Pour plus d’informations, consultez [traduction d’opérateur de requête standard](standard-query-operator-translation.md).  
  
## <a name="memory-issues"></a>Problèmes de mémoire  

 Si une requête implique une collection en mémoire et [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> , la requête peut être exécutée en mémoire, selon l’ordre dans lequel les deux collections sont spécifiées. Si la requête doit être exécutée dans la mémoire, les données de la table de base de données devront être extraites.  
  
 Cette approche est inefficace et peut se traduire par une utilisation significative de la mémoire et du processeur. Essayez d'éviter de telles requêtes multidomaines.  
  
## <a name="file-names-and-sqlmetal"></a>Noms de fichier et SQLMetal  

 Pour spécifier un nom de fichier d'entrée, ajoutez son nom à la ligne de commande comme fichier d'entrée. L’inclusion du nom de fichier dans la chaîne de connexion (avec l’option **/conn** ) n’est pas prise en charge. Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="class-library-projects"></a>Projets de bibliothèque de classe  

 L’Concepteur Objet Relationnel crée une chaîne de connexion dans le `app.config` fichier du projet. Dans les projets de bibliothèque de classes, le fichier `app.config` n'est pas utilisé. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] utilise la chaîne de connexion fournie dans les fichiers au moment du design. La modification de la valeur dans `app.config` ne modifie pas la base de données à laquelle votre application se connecte.  
  
## <a name="cascade-delete"></a>Suppression en cascade  

 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ne prend pas en charge ni ne reconnaît les opérations de suppression en cascade. Si vous souhaitez supprimer une ligne dans une table comportant des contraintes sur cette suppression, vous devez effectuer l'une des actions suivantes :  
  
- Définissez la règle `ON DELETE CASCADE` dans la contrainte de clé étrangère dans la base de données.  
  
- Utilisez votre propre code pour supprimer en premier les objets enfants qui empêchent la suppression de l'objet parent.  
  
 Sinon, une exception <xref:System.Data.SqlClient.SqlException> est levée.  
  
 Pour plus d’informations, consultez [Comment : supprimer des lignes de la base de données](how-to-delete-rows-from-the-database.md).  
  
## <a name="expression-not-queryable"></a>Expression non requêtable  

 Si vous obtenez l'erreur "L'expression de type [expression] ne peut pas être interrogée. Vérifiez que vous n'omettez pas une référence d'assembly et/ou une importation d'espace de noms pour le fournisseur LINQ." , vérifiez que :  
  
- Votre application cible .NET Compact Framework 3,5.  
  
- Il y a une référence à `System.Core.dll` et `System.Data.Linq.dll`.  
  
- Vous avez une `Imports` directive (Visual Basic) ou `using` (C#) pour <xref:System.Linq> et <xref:System.Data.Linq> .  
  
## <a name="duplicatekeyexception"></a>DuplicateKeyException  

 Au cours du débogage d’un [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projet, vous pouvez parcourir les relations d’une entité. Cela permet d’intégrer ces éléments dans le cache et [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] de connaître leur présence. Si vous tentez ensuite d'exécuter <xref:System.Data.Linq.Table%601.Attach%2A> ou <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> ou une méthode similaire qui produit plusieurs lignes ayant la même clé, une <xref:System.Data.Linq.DuplicateKeyException> est levée.  
  
## <a name="string-concatenation-exceptions"></a>Exceptions de concaténation de chaînes  

 La concaténation sur les opérandes mappées à `[n]text` et d'autre `[n][var]char` n'est pas prise en charge. Une exception est levée en cas de concaténation de chaînes mappée à deux ensembles de types différents. Pour plus d’informations, consultez [System. String, méthodes](system-string-methods.md).  
  
## <a name="skip-and-take-exceptions-in-sql-server-2000"></a>Exceptions d'ignorance (Skip) et d'acceptation (Take) dans SQL Server 2000  

 Vous devez utiliser des membres d'identité (<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>) lorsque vous utilisez <xref:System.Linq.Queryable.Take%2A> ou <xref:System.Linq.Queryable.Skip%2A> sur une base de données Microsoft SQL Server 2000. La requête doit être effectuée sur une table unique (c'est-à-dire, pas une jointure) ou il doit s'agir d'une opération <xref:System.Linq.Queryable.Distinct%2A>, <xref:System.Linq.Queryable.Except%2A>, <xref:System.Linq.Queryable.Intersect%2A> ou <xref:System.Linq.Queryable.Union%2A>, et elle ne doit pas inclure d'opération <xref:System.Linq.Queryable.Concat%2A>. Pour plus d’informations, consultez la section « prise en charge de SQL Server 2000 » dans [traduction d’opérateur de requête standard](standard-query-operator-translation.md).  
  
 Cette exigence ne s’applique pas à SQL Server 2005.  
  
## <a name="groupby-invalidoperationexception"></a>GroupBy InvalidOperationException  

 Cette exception est levée lorsqu'une valeur de colonne est null dans une requête <xref:System.Linq.Enumerable.GroupBy%2A> regroupée par une expression `boolean`, telle que `group x by (Phone==@phone)`. Étant donné que l’expression est un `boolean` , la clé est déduite comme étant `boolean` , et non `nullable` `boolean` . Lorsque la comparaison traduite produit une valeur null, une tentative est faite pour assigner un `nullable` `boolean` à un `boolean` , et l’exception est levée.  
  
 Pour éviter cette situation (en supposant que vous souhaitiez traiter les valeurs null comme des valeurs false), utilisez, par exemple, la méthode suivante :  
  
 `GroupBy="(Phone != null) && (Phone=@Phone)"`  
  
## <a name="oncreated-partial-method"></a>Méthode partielle OnCreated()  

 La méthode générée `OnCreated()` est appelée chaque fois que le constructeur d'objet est appelé, y compris dans le cas où [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] appelle le constructeur pour faire une copie pour les valeurs d'origine. Tenez compte de ce comportement si vous implémentez la méthode `OnCreated()` dans votre propre classe partielle.  
  
## <a name="see-also"></a>Voir aussi

- [Prise en charge du débogage](debugging-support.md)
- [Questions fréquentes (FAQ)](frequently-asked-questions.md)
