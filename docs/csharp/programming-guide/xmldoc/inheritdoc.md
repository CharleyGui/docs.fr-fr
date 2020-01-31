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
ms.openlocfilehash: d660cb1739733c4e98ae0b7939476fe74e6cf200
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76795160"
---
# <a name="inheritdoc-c-programming-guide"></a>\<inheritdoc > (C# Guide de programmation)

## <a name="syntax"></a>Syntaxe  
  
```xml  
<inheritdoc/> 
```  

## <a name="inheritdoc"></a>InheritDoc

Hériter des commentaires XML à partir des classes de base, des interfaces et des méthodes similaires. Cela élimine la copie et le collage indésirables de commentaires XML en double et conserve automatiquement les commentaires XML synchronisés. 
  
## <a name="remarks"></a>Notes  
Ajoutez vos commentaires XML dans des classes ou des interfaces de base et laissez InheritDoc copier les commentaires vers les classes d’implémentation.

Ajoutez vos commentaires XML à vos méthodes synchrones et laissez InheritDoc copier les commentaires dans vos versions asynchrones des mêmes méthodes.  

Si vous souhaitez copier les commentaires à partir d’un membre spécifique, vous pouvez utiliser l’attribut `cref` pour spécifier le membre.
  
## <a name="examples"></a>Exemples
[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md)
