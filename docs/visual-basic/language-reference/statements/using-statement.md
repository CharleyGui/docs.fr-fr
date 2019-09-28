---
title: Using, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
ms.openlocfilehash: 819af63acb6a1f038300bcb999dcfb904eb8a457
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592089"
---
# <a name="using-statement-visual-basic"></a>Using, instruction (Visual Basic)

Déclare le début d’un bloc `Using` et acquiert éventuellement les ressources système que le bloc contrôle.

## <a name="syntax"></a>Syntaxe

```vb
Using { resourcelist | resourceexpression }
    [ statements ]
End Using
```

## <a name="parts"></a>Composants

|Terme|Définition|  
|---|---|  
|`resourcelist`|Obligatoire si vous ne fournissez pas `resourceexpression`. Liste d’une ou plusieurs ressources système que ce `Using` contrôle de bloc, séparées par des virgules.|  
|`resourceexpression`|Obligatoire si vous ne fournissez pas `resourcelist`. Variable ou expression de référence faisant référence à une ressource système pour être contrôlée par ce bloc `Using`.|  
|`statements`|facultatif. Bloc d’instructions exécutées par le bloc `Using`.|  
|`End Using`|Obligatoire. Met fin à la définition du bloc `Using` et supprime toutes les ressources qu’il contrôle.|  

 Chaque ressource de la partie `resourcelist` possède la syntaxe et les éléments suivants :

 `resourcename As New resourcetype [ ( [ arglist ] ) ]`

 \- ou -

 `resourcename As resourcetype = resourceexpression`

## <a name="resourcelist-parts"></a>Composants ResourceList

|Terme|Définition|  
|---|---|  
|`resourcename`|Obligatoire. Variable de référence qui fait référence à une ressource système que le bloc `Using` contrôle.|  
|`New`|Obligatoire si l’instruction `Using` acquiert la ressource. Si vous avez déjà acquis la ressource, utilisez la deuxième syntaxe.|  
|`resourcetype`|Obligatoire. Classe de la ressource. La classe doit implémenter l’interface <xref:System.IDisposable>.|  
|`arglist`|facultatif. Liste des arguments que vous passez au constructeur pour créer une instance de `resourcetype`. Consultez la [liste des paramètres](parameter-list.md).|  
|`resourceexpression`|Obligatoire. Variable ou expression faisant référence à une ressource système répondant aux exigences de `resourcetype`. Si vous utilisez la deuxième syntaxe, vous devez acquérir la ressource avant de passer le contrôle à l’instruction `Using`.|  
  
## <a name="remarks"></a>Notes

 Parfois, votre code requiert une ressource non managée, telle qu’un descripteur de fichier, un wrapper COM ou une connexion SQL. Un bloc `Using` garantit la suppression d’une ou de plusieurs de ces ressources lorsque votre code est terminé. Cela les rend disponibles pour le code à utiliser.

 Les ressources managées sont supprimées par le garbage collector .NET Framework (GC) sans codage supplémentaire de votre part. Vous n’avez pas besoin d’un bloc `Using` pour les ressources managées. Toutefois, vous pouvez toujours utiliser un bloc `Using` pour forcer la suppression d’une ressource managée au lieu d’attendre le garbage collector.

 Un bloc `Using` comporte trois parties : l’acquisition, l’utilisation et la suppression.

- L' *acquisition* consiste à créer une variable et à l’initialiser pour faire référence à la ressource système. L’instruction `Using` peut acquérir une ou plusieurs ressources, ou vous pouvez acquérir une seule ressource avant d’entrer dans le bloc et la fournir à l’instruction `Using`. Si vous fournissez `resourceexpression`, vous devez acquérir la ressource avant de passer le contrôle à l’instruction `Using`.

- *L’utilisation* consiste à accéder aux ressources et à effectuer des actions avec eux. Les instructions entre `Using` et `End Using` représentent l’utilisation des ressources.

- La *suppression* consiste à appeler la méthode <xref:System.IDisposable.Dispose%2A> sur l’objet dans `resourcename`. Cela permet à l’objet de terminer correctement ses ressources. L’instruction `End Using` supprime les ressources sous le contrôle du bloc `Using`.

## <a name="behavior"></a>Comportement

 Un bloc `Using` se comporte comme une construction `Try`... `Finally` dans laquelle le bloc `Try` utilise les ressources et le bloc `Finally` les supprime. Pour cette raison, le bloc `Using` garantit la suppression des ressources, quel que soit le mode de sortie du bloc. Cela est vrai même dans le cas d’une exception non gérée, à l’exception d’un <xref:System.StackOverflowException>.

 La portée de chaque variable de ressource acquise par l’instruction `Using` est limitée au bloc `Using`.

 Si vous spécifiez plusieurs ressources système dans l’instruction `Using`, l’effet est le même que si vous imbriquez `Using` blocs dans un autre.

 Si `resourcename` est `Nothing`, aucun appel à <xref:System.IDisposable.Dispose%2A> n’est effectué et aucune exception n’est levée.

## <a name="structured-exception-handling-within-a-using-block"></a>Gestion structurée des exceptions dans un bloc using

 Si vous devez gérer une exception qui peut se produire dans le bloc `Using`, vous pouvez ajouter une construction complète `Try`... `Finally`. Si vous devez gérer le cas où l’instruction `Using` ne parvient pas à acquérir une ressource, vous pouvez effectuer un test pour voir si `resourcename` est `Nothing`.

## <a name="structured-exception-handling-instead-of-a-using-block"></a>Gestion structurée des exceptions à la place d’un bloc using

 Si vous avez besoin d’un contrôle plus fin sur l’acquisition des ressources ou si vous avez besoin de code supplémentaire dans le bloc `Finally`, vous pouvez réécrire le bloc `Using` en tant que construction `Try`... `Finally`. L’exemple suivant montre les constructions squelettes `Try` et `Using` qui sont équivalentes dans l’acquisition et la suppression de `resource`.

```vb
Using resource As New resourceType
    ' Insert code to work with resource.
End Using

' For the acquisition and disposal of resource, the following  
' Try construction is equivalent to the Using block.
Dim resource As New resourceType
Try
    ' Insert code to work with resource.
Finally
    If resource IsNot Nothing Then
        resource.Dispose()
    End If
End Try
```

> [!NOTE]
> Le code à l’intérieur du bloc `Using` ne doit pas assigner l’objet dans `resourcename` à une autre variable. Lorsque vous quittez le bloc `Using`, la ressource est supprimée et l’autre variable ne peut pas accéder à la ressource vers laquelle elle pointe.

## <a name="example"></a>Exemple

 L’exemple suivant crée un fichier nommé log. txt et écrit deux lignes de texte dans le fichier. L’exemple lit également le même fichier et affiche les lignes de texte :

 Étant donné que les classes <xref:System.IO.TextWriter> et <xref:System.IO.TextReader> implémentent l’interface <xref:System.IDisposable>, le code peut utiliser des instructions `Using` pour s’assurer que le fichier est fermé correctement après les opérations d’écriture et de lecture.

 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]

## <a name="see-also"></a>Voir aussi

- <xref:System.IDisposable>
- [Try...Catch...Finally (instruction)](try-catch-finally-statement.md)
- [Guide pratique pour Supprimer une ressource système @ no__t-0
