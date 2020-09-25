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
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="1cd93-102">Procédure : Rendre les entités sérialisables</span><span class="sxs-lookup"><span data-stu-id="1cd93-102">How to: Make Entities Serializable</span></span>

<span data-ttu-id="1cd93-103">Vous pouvez rendre des entités sérialisables lorsque vous générez votre code.</span><span class="sxs-lookup"><span data-stu-id="1cd93-103">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="1cd93-104">Les classes d'entité sont décorées avec l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> et les colonnes avec l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute>.</span><span class="sxs-lookup"><span data-stu-id="1cd93-104">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="1cd93-105">Les développeurs qui utilisent Visual Studio peuvent utiliser le Concepteur Objet Relationnel à cet effet.</span><span class="sxs-lookup"><span data-stu-id="1cd93-105">Developers using Visual Studio can use the Object Relational Designer for this purpose.</span></span>  
  
 <span data-ttu-id="1cd93-106">Si vous utilisez l’outil en ligne de commande SQLMetal, utilisez l’option **/Serialization** avec l' `unidirectional` argument.</span><span class="sxs-lookup"><span data-stu-id="1cd93-106">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="1cd93-107">Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="1cd93-107">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1cd93-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="1cd93-108">Example</span></span>  

 <span data-ttu-id="1cd93-109">Les lignes de commande SQLMetal suivantes produisent des fichiers qui ont des entités sérialisables.</span><span class="sxs-lookup"><span data-stu-id="1cd93-109">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```console  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```console  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="1cd93-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1cd93-110">See also</span></span>

- [<span data-ttu-id="1cd93-111">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="1cd93-111">Serialization</span></span>](serialization.md)
- [<span data-ttu-id="1cd93-112">Création du modèle objet</span><span class="sxs-lookup"><span data-stu-id="1cd93-112">Creating the Object Model</span></span>](creating-the-object-model.md)
