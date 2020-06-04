---
title: <list>
ms.date: 07/20/2015
helpviewer_keywords:
- listheader XML tag
- <item> XML tag
- <list> XML tag
- <listheader> XML tag
- term XML tag
- list XML tag
- <description> XML tag
- description XML tag
- item XML tag
- <term> XML tag
ms.assetid: ec35fced-d58e-4520-a764-0691256e014b
ms.openlocfilehash: 955c1a4c5c5619f908b8d03dbf12360c23574478
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400084"
---
# <a name="list-visual-basic"></a>\<list> (Visual Basic)
Définit une liste ou une table.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<list type="type">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
## <a name="parameters"></a>Paramètres  
 `type`  
 Type de la liste. Doit être une « puce » pour une liste à puces, « nombre » pour une liste numérotée ou « table » pour une table à deux colonnes.  
  
 `term`  
 Utilisé uniquement lorsque `type` est « table ». Terme à définir, qui est défini dans la balise de description.  
  
 `description`  
 Lorsque est `type` « Bullet » ou « Number », `description` est un élément de la liste lorsque `type` est « table », `description` est la définition de `term` .  
  
## <a name="remarks"></a>Notes  
 Le `<listheader>` bloc définit le titre d’une table ou d’une liste de définitions. Lors de la définition d’une table, il vous suffit de fournir une entrée pour `term` dans l’en-tête.  
  
 Chaque élément de la liste est spécifié avec un `<item>` bloc. Lorsque vous créez une liste de définitions, vous devez spécifier à la fois `term` et `description` . Toutefois, pour une table, une liste à puces ou une liste numérotée, il vous suffit de fournir une entrée pour `description` .  
  
 Une liste ou une table peut avoir autant de `<item>` blocs que nécessaire.  
  
 Compilez avec [-doc](../../reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la `<list>` balise pour définir une liste à puces dans la section Notes.  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>Voir aussi

- [Étiquettes XML pour les commentaires](index.md)
