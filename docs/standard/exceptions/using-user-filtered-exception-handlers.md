---
title: Utiliser des gestionnaires d’exceptions filtrés par l’utilisateur
description: Découvrez comment utiliser des gestionnaires d’exceptions filtrés par l’utilisateur en C# et Visual Basic.
ms.date: 12/14/2020
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
dev_langs:
- csharp
- vb
ms.openlocfilehash: 2dba43ad2fc685a6555ab43fc973814fd7f359a3
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512669"
---
# <a name="use-user-filtered-exception-handlers"></a>Utiliser des gestionnaires d’exceptions filtrés par l’utilisateur

Les gestionnaires d’exceptions filtrés par l’utilisateur interceptent et gèrent les exceptions selon des critères que vous définissez pour l’exception. Ces gestionnaires utilisent l' `catch` instruction avec le `when` mot clé ( `Catch` et `When` dans Visual Basic).  
  
 Cette technique est utile lorsqu’un objet d’exception particulier correspond à plusieurs erreurs. Dans ce cas, l’objet possède généralement une propriété qui contient le code d’erreur associé à l’erreur. Vous pouvez utiliser la propriété code d’erreur dans l’expression pour sélectionner uniquement l’erreur particulière que vous souhaitez gérer dans cette `catch` clause.  
  
 L’exemple suivant illustre l' `catch` / `when` instruction.

```csharp
try
{
    //Try statements.  
}
catch (Exception ex) when (ex.Message.Contains("404"))
{
    //Catch statements.
}
```  
  
```vb
Try  
    'Try statements.  
    Catch When Err = VBErr_ClassLoadException
    'Catch statements.
End Try  
```  
  
 L’expression de la clause filtrée par l’utilisateur n’est pas limitée. Si une exception se produit pendant l’exécution de l’expression filtrée par l’utilisateur, cette exception est ignorée et l’expression filtrée est considérée comme ayant la valeur False. Dans ce cas, le common language runtime continue la recherche d’un gestionnaire pour l’exception actuelle.  
  
## <a name="combine-the-specific-exception-and-the-user-filtered-clauses"></a>Combiner l’exception spécifique et les clauses filtrées par l’utilisateur  

 Une `catch` instruction peut contenir à la fois l’exception spécifique et les clauses filtrées par l’utilisateur. Le runtime teste tout d’abord l’exception spécifique. Si l’exception spécifique réussit, le runtime exécute le filtre de l’utilisateur. Le filtre générique peut contenir une référence à la variable déclarée dans le filtre de la classe. Notez que l’ordre des deux clauses de filtre ne peut pas être inversé.  
  
 L’exemple suivant montre une exception spécifique dans l’instruction **catch** , ainsi que la clause filtrée par l’utilisateur à l’aide du mot clé **When** .  
  
```csharp
try
{
    //Try statements.  
}
catch (System.Net.Http.HttpRequestException ex) when (ex.Message.Contains("404"))
{
    //Catch statements.
}
```  
  
```vb
Try  
    'Try statements.
    Catch cle As ClassLoadException When cle.IsRecoverable()  
    'Catch statements.
End Try  
```  

## <a name="see-also"></a>Voir aussi

- [Exceptions](index.md)
