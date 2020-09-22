---
title: Le nom '<name>' n'est pas déclaré
ms.date: 10/10/2018
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
ms.openlocfilehash: 76c1ab4fb5f1f8e4c76a06110f4b0f9026cca201
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871549"
---
# <a name="name-name-is-not-declared"></a>Le nom '\<name>' n'est pas déclaré

Une instruction fait référence à un élément de programmation, mais le compilateur ne peut pas trouver un élément avec ce nom exact.  
  
 **ID d’erreur :** BC30451  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Vérifiez l’orthographe du nom dans l’instruction de référence. Visual Basic ne respecte pas la casse, mais toute autre variation de l’orthographe est considérée comme un nom complètement différent. Notez que le caractère de soulignement (`_`) fait partie du nom et donc de l’orthographe.  
  
2. Vérifiez que vous disposez de l’opérateur d’accès aux membres ( `.` ) entre un objet et son membre. Par exemple, si vous disposez d’un contrôle <xref:System.Windows.Forms.TextBox> dont le nom est `TextBox1`, pour accéder à sa propriété <xref:System.Windows.Forms.TextBoxBase.Text%2A> , vous devez taper `TextBox1.Text`. Si, au lieu de cela, vous tapez `TextBox1Text`, vous créez un nom différent.  
  
3. Si l’orthographe est correcte et que la syntaxe de tout accès aux membres de l’objet est correcte, vérifiez que l’élément a été déclaré. Pour plus d’informations, consultez [éléments déclarés](../../programming-guide/language-features/declared-elements/index.md).  
  
4. Si l’élément de programmation a été déclaré, vérifiez qu’il est dans la portée. Si l’instruction de référence est en dehors de la région déclarant l’élément de programmation, vous devrez peut-être qualifier le nom de l’élément. Pour plus d'informations, consultez [Scope in Visual Basic](../../programming-guide/language-features/declared-elements/scope.md).  

5. Si vous n’utilisez pas un type qualifié complet ou un nom de type et de membre (par exemple, votre code fait référence à une propriété au `MethodInfo.Name` lieu de `System.Reflection.MethodInfo.Name` ), ajoutez une [instruction Imports](../statements/imports-statement-net-namespace-and-type.md).

6. Si vous essayez de compiler un projet de type SDK (un projet avec un \* fichier. vbproj qui commence par la ligne `<Project Sdk="Microsoft.NET.Sdk">` ) et que le message d’erreur fait référence à un type ou un membre de l’assembly Microsoft.VisualBasic.dll, configurez votre application pour qu’elle soit compilée avec une référence à la bibliothèque d’exécution Visual Basic. Par défaut, un sous-ensemble de la bibliothèque est incorporé dans votre assembly dans un projet de type SDK.

   Par exemple, la compilation de l’exemple suivant échoue, car la <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ChangeType%2A?displayProperty=fullName> méthode est introuvable. Il n’est pas incorporé dans le sous-ensemble du runtime Visual Basic inclus avec votre application.  

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/program1.vb?highlight=7)]

   Pour résoudre cette erreur, ajoutez l' `<VBRuntime>Default</VBRuntime>` élément à la `<PropertyGroup>` section projets, comme le montre le fichier de projet Visual Basic suivant.

   [!code-xml[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/vbruntime.vbproj?highlight=6)]

## <a name="see-also"></a>Voir aussi

- [Liste des déclarations et des constantes](../keywords/declarations-and-constants-summary.md)
- [Conventions d'affectation de noms Visual Basic](../../programming-guide/program-structure/naming-conventions.md)
- [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
