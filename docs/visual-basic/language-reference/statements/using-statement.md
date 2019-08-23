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
ms.openlocfilehash: 346a26ad5751599831d8b0d3e0497e4d488eb76c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957547"
---
# <a name="using-statement-visual-basic"></a>Using, instruction (Visual Basic)
Déclare le début d’un `Using` bloc et acquiert éventuellement les ressources système que le bloc contrôle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`resourcelist`|Obligatoire si vous ne fournissez `resourceexpression`pas. Liste d’une ou plusieurs ressources système que ce `Using` bloc contrôle, séparées par des virgules.|  
|`resourceexpression`|Obligatoire si vous ne fournissez `resourcelist`pas. Variable ou expression de référence faisant référence à une ressource système pour être contrôlée `Using` par ce bloc.|  
|`statements`|facultatif. Bloc d’instructions exécutées `Using` par le bloc.|  
|`End Using`|Requis. Met fin à la définition du `Using` bloc et supprime toutes les ressources qu’il contrôle.|  
  
 Chaque ressource de la `resourcelist` partie possède la syntaxe et les éléments suivants:  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 ou  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a>Composants ResourceList  
  
|Terme|Définition|  
|---|---|  
|`resourcename`|Requis. Variable de référence qui fait référence à une ressource système `Using` que le bloc contrôle.|  
|`New`|Obligatoire si l' `Using` instruction acquiert la ressource. Si vous avez déjà acquis la ressource, utilisez la deuxième syntaxe.|  
|`resourcetype`|Requis. Classe de la ressource. La classe doit implémenter <xref:System.IDisposable> l’interface.|  
|`arglist`|facultatif. Liste des arguments que vous passez au constructeur pour créer une instance de `resourcetype`. Consultez la [liste des paramètres](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`resourceexpression`|Requis. Variable ou expression faisant référence à une ressource système répondant aux exigences `resourcetype`de. Si vous utilisez la deuxième syntaxe, vous devez acquérir la ressource avant de passer le contrôle à `Using` l’instruction.|  
  
## <a name="remarks"></a>Notes  
 Parfois, votre code requiert une ressource non managée, telle qu’un descripteur de fichier, un wrapper COM ou une connexion SQL. Un `Using` bloc garantit la suppression d’une ou de plusieurs de ces ressources lorsque votre code est terminé. Cela les rend disponibles pour le code à utiliser.  
  
 Les ressources managées sont supprimées par le garbage collector .NET Framework (GC) sans codage supplémentaire de votre part. Vous n’avez pas besoin `Using` d’un bloc pour les ressources managées. Toutefois, vous pouvez toujours utiliser un `Using` bloc pour forcer la suppression d’une ressource managée au lieu d’attendre le garbage collector.  
  
 Un `Using` bloc comporte trois parties: l’acquisition, l’utilisation et la suppression.  
  
- L' *acquisition* consiste à créer une variable et à l’initialiser pour faire référence à la ressource système. L' `Using` instruction peut acquérir une ou plusieurs ressources, ou vous pouvez acquérir une seule ressource avant d’entrer dans le bloc et la fournir `Using` à l’instruction. Si vous fournissez `resourceexpression`, vous devez acquérir la ressource avant de passer le `Using` contrôle à l’instruction.  
  
- *L’utilisation* consiste à accéder aux ressources et à effectuer des actions avec eux. Les instructions entre `Using` et `End Using` représentent l’utilisation des ressources.  
  
- La *suppression* consiste à <xref:System.IDisposable.Dispose%2A> appeler la méthode sur l' `resourcename`objet dans. Cela permet à l’objet de terminer correctement ses ressources. L' `End Using` instruction supprime les ressources sous le `Using` contrôle du bloc.  
  
## <a name="behavior"></a>Comportement  
 Un `Using` bloc se comporte comme un `Try`... construction dans laquelle le `Try` bloc utilise les ressources et le `Finally` bloc les supprime. `Finally` Pour cette raison, le `Using` bloc garantit la suppression des ressources, quel que soit le mode de sortie du bloc. Cela est vrai même dans le cas d’une exception non gérée, à l’exception <xref:System.StackOverflowException>de.  
  
 La portée de chaque variable de ressource acquise `Using` par l’instruction est limitée `Using` au bloc.  
  
 Si vous spécifiez plusieurs ressources système dans l’instruction `Using` , l’effet est le même que si vous `Using` imbriquez des blocs l’un dans l’autre.  
  
 Si `resourcename` a `Nothing`la valeur, aucun <xref:System.IDisposable.Dispose%2A> appel à n’est effectué et aucune exception n’est levée.  
  
## <a name="structured-exception-handling-within-a-using-block"></a>Gestion structurée des exceptions dans un bloc using  
 Si vous devez gérer une exception qui peut se produire dans le `Using` bloc, vous pouvez ajouter une opération `Try`... `Finally` . Si vous devez gérer le cas où l' `Using` instruction ne parvient pas à acquérir une ressource, vous pouvez effectuer un test pour voir si `Nothing` `resourcename` est.  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a>Gestion structurée des exceptions à la place d’un bloc using  
 Si vous avez besoin d’un `Finally` `Try`contrôle plus fin sur l’acquisition des ressources ou si vous avez besoin de code supplémentaire dans le bloc, `Using` vous pouvez réécrire le bloc en tant que... `Finally` construction. L’exemple suivant montre le `Try` squelette `Using` et les constructions qui sont équivalents dans l’acquisition et `resource`la suppression de.  
  
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
> Le code à l' `Using` intérieur du bloc ne doit pas assigner l’objet dans `resourcename` à une autre variable. Lorsque vous quittez `Using` le bloc, la ressource est supprimée et l’autre variable ne peut pas accéder à la ressource vers laquelle elle pointe.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée un fichier nommé log. txt et écrit deux lignes de texte dans le fichier. L’exemple lit également le même fichier et affiche les lignes de texte.  
  
 Étant donné <xref:System.IO.TextWriter> que <xref:System.IO.TextReader> les classes et <xref:System.IDisposable> implémentent l’interface, le `Using` code peut utiliser des instructions pour s’assurer que le fichier est fermé correctement après les opérations d’écriture et de lecture.  
  
 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IDisposable>
- [Try...Catch...Finally (instruction)](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Guide pratique pour Supprimer une ressource système](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
