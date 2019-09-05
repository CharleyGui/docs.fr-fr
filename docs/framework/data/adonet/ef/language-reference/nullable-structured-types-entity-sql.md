---
title: Types structurés autorisant la valeur null (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: 6b078ae458aba73e82957f84408b1000b216aef9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249812"
---
# <a name="nullable-structured-types-entity-sql"></a>Types structurés autorisant la valeur null (Entity SQL)
Une instance `null` d'un type structuré est une instance qui n'existe pas. Cela est différent d'une instance existante dans laquelle toutes les propriétés ont des valeurs `null`.  
  
 Cette rubrique décrit les types structurés Nullable, y compris quels types sont Nullable et quels modèles de code produisent des instances `null` de types Nullable structurés.  
  
## <a name="kinds-of-nullable-structured-types"></a>Différents types structurés Nullable  
 Il existe trois sortes de types de structure Nullable :  
  
- Types de ligne  
  
- Types complexes.  
  
- types d'entités  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a>Modèles de code qui produisent des instances Null de types structurés  
 Les scénarios suivants produisent des instances `null` :  
  
- Mise en forme de données `null` comme type structuré :  
  
    ```  
    TREAT (NULL AS StructuredType)  
    ```  
  
- Upcast d'un type de base vers un type dérivé :  
  
    ```  
    TREAT (BaseType AS DerivedType)  
    ```  
  
- Jointure externe sur condition fausse :  
  
    ```  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     -- ou  
  
    ```  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     -- ou  
  
    ```  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
- Suppression d'une référence `null` :  
  
    ```  
    DEREF(NullRef)  
    ```  
  
- Obtention d’ANYELEMENT à partir d’une collection vide :  
  
    ```  
    ANYELEMENT(EmptyCollection)  
    ```  
  
- Recherche d'instances `null` de types structurés :  
  
    ```csharp  
    ...  
    for (int i = 0; i < reader.FieldCount; i++)  
    {  
        if (reader.IsDBNull(i))  
        {  
            Console.WriteLine("[NULL]");  
        }  
        else  
        {  
            Console.WriteLine(reader.GetValue(i).ToString());  
        }  
    }  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble d’Entity SQL](entity-sql-overview.md)
