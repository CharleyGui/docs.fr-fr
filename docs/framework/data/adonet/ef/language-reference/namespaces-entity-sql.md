---
title: Espaces de noms (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
ms.openlocfilehash: 7f05067c4bdb859f3661f775c2502852b6658522
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319562"
---
# <a name="namespaces-entity-sql"></a>Espaces de noms (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] introduit les espaces de noms afin d'éviter les conflits de noms des identificateurs globaux tels que les noms de types, les jeux d'entités, les fonctions, etc. La prise en charge de l’espace de noms dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] est semblable à la prise en charge des espaces de noms dans le .NET Framework.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fournit deux formes de la clause USING : les espaces de noms qualifiés (où un alias plus court est fourni pour l'espace de noms) et les espaces de noms non qualifiés, tels qu'illustrés dans l'exemple suivant :  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a>Règles de résolution de noms  
 Si un identificateur ne peut pas être résolu dans les portées locales, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tente de localiser le nom dans les portées globales (les espaces de noms). [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tente tout d'abord de faire correspondre l'identificateur (préfixe) avec l'un des espaces de noms qualifiés. En cas de correspondance, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tente de résoudre le reste de l’identificateur dans l’espace de noms spécifié. Si aucune correspondance n'est trouvée, une exception est levée.  
  
 Ensuite, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tente de Rechercher l’identificateur dans tous les espaces de noms non qualifiés (spécifiés dans le prologue). Si l'identificateur est localisé dans exactement un espace de noms, cet emplacement est retourné. Si plusieurs espaces de noms ont une correspondance pour cet identificateur, une exception est levée. Si aucun espace de noms ne peut être identifié pour l’identificateur, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] passe le nom à l’étendue externe suivante (l’objet <xref:System.Data.Common.DbCommand> ou <xref:System.Data.Common.DbConnection>), comme illustré dans l’exemple suivant :  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a>Différences par rapport au .NET Framework  
 Dans le .NET Framework, vous pouvez utiliser des espaces de noms partiellement qualifiés. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne permet pas cela.  
  
## <a name="adonet-usage"></a>Utilisation d'ADO.NET  
 Les requêtes sont exprimées par le biais d'objets <xref:System.Data.Common.DbCommand> ADO.NET. Les objets <xref:System.Data.Common.DbCommand> peuvent être créés à partir d'objets <xref:System.Data.Common.DbConnection>. Il est également possible de spécifier des espaces de noms comme faisant partie des objets <xref:System.Data.Common.DbCommand> et <xref:System.Data.Common.DbConnection>. Si [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne peut pas résoudre un identificateur dans la requête elle-même, les espaces de noms externes sont détectés (selon des règles similaires).  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
- [Vue d’ensemble d’Entity SQL](entity-sql-overview.md)
