---
title: Comment afficher les arguments de la ligne de commande - Guide de programmation C
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 210dad71220572535a0325fac925b0453b0d4e03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712024"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>Comment afficher les arguments de la ligne de commande (Guide de programmation CMD)
Les arguments fournis à un fichier exécutable sur la ligne de commande sont accessibles à `Main` par l’intermédiaire d’un paramètre facultatif. Les arguments sont fournis sous la forme d’un tableau de chaînes. Chaque élément du tableau contient un argument. Les espaces blancs entre arguments sont supprimés. Par exemple, considérez ces appels de ligne de commande d’un fichier exécutable fictif :  
  
|Entrée sur la ligne de commande|Tableau de chaînes passé à Main|  
|----------------------------|-------------------------------------|  
|**executable.exe a b c**|"a"<br /><br /> "b"<br /><br /> "c"|  
|**executable.exe un deux**|"un"<br /><br /> "deux"|  
|**executable.exe "un deux" trois**|"un deux"<br /><br /> "trois"|  
  
> [!NOTE]
> Quand vous exécutez une application dans Visual Studio, vous pouvez spécifier des arguments de ligne de commande dans la [page Déboguer du Concepteur de projets](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a> Exemple  
 Cet exemple affiche les arguments de ligne de commande passés à une application de ligne de commande. La sortie présentée concerne la première entrée du tableau ci-dessus.  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Génération en ligne de commande avec csc.exe](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Main() et arguments de ligne de commande](./index.md)
- [Valeurs de retour Main()](./main-return-values.md)
