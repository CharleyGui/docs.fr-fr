---
title: 'Procédure : Rendre les entités sérialisables'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: f4528cab21ac678f5d06717d0ce6e7ff7e77d3e4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203499"
---
# <a name="how-to-make-entities-serializable"></a>Procédure : Rendre les entités sérialisables

Vous pouvez rendre des entités sérialisables lorsque vous générez votre code. Les classes d'entité sont décorées avec l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> et les colonnes avec l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute>.  
  
 Les développeurs qui utilisent Visual Studio peuvent utiliser le Concepteur Objet Relationnel à cet effet.  
  
 Si vous utilisez l’outil en ligne de commande SQLMetal, utilisez l’option **/Serialization** avec l' `unidirectional` argument. Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Exemple  

 Les lignes de commande SQLMetal suivantes produisent des fichiers qui ont des entités sérialisables.  
  
```console  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```console  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a>Voir aussi

- [Sérialisation](serialization.md)
- [Création du modèle objet](creating-the-object-model.md)
