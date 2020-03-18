---
title: <inheritdoc> - Guide de programmation C#
ms.date: 01/21/2020
f1_keywords:
- inheritdoc
- <inheritdoc>
helpviewer_keywords:
- <inheritdoc> C# XML tag
- inheritdoc C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 6f42462f21d045428577cd2123e2180d866f1e1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156946"
---
# <a name="inheritdoc-c-programming-guide"></a>\<inheritdoc> (Guide de programmation de C)

## <a name="syntax"></a>Syntaxe  
  
```xml  
<inheritdoc/>
```  

## <a name="inheritdoc"></a>InheritDoc

Héritez des commentaires XML des classes de base, des interfaces et des méthodes similaires. Cela élimine la copie et le coller indésirables des commentaires XML en double et maintient automatiquement les commentaires XML synchronisés.
  
## <a name="remarks"></a>Notes   
Ajoutez vos commentaires XML dans des classes de base ou des interfaces et laissez InheritDoc copier les commentaires aux classes de mise en œuvre.

Ajoutez vos commentaires XML à vos méthodes synchrones et laissez InheritDoc copier les commentaires à vos versions asynchrones des mêmes méthodes.  

Si vous souhaitez copier les commentaires d’un `cref` membre spécifique, vous pouvez utiliser l’attribut pour spécifier le membre.
  
## <a name="examples"></a>Exemples
[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Tags recommandés pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md)
