---
title: Liaison anticipée et liaison tardive
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- objects [Visual Basic], late-bound
- objects [Visual Basic], early-bound
- objects [Visual Basic], late bound
- early binding [Visual Basic], Visual Basic compiler
- binding [Visual Basic], late and early
- objects [Visual Basic], early bound
- Visual Basic compiler, early and late binding
- late binding [Visual Basic]
- late binding [Visual Basic], Visual Basic compiler
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
ms.openlocfilehash: e8d87e095b7c3104e3a2d66525644d1771ae883e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410630"
---
# <a name="early-and-late-binding-visual-basic"></a>Liaison anticipée et liaison tardive (Visual Basic)
Le compilateur Visual Basic exécute un processus appelé `binding` lorsqu’un objet est assigné à une variable objet. Un objet est dit *à liaison anticipée* lorsqu’il est affecté à une variable déclarée comme étant d’un type d’objet spécifique. Les objets à liaison anticipée permettent au compilateur d’allouer de la mémoire et d’effectuer d’autres optimisations avant l’exécution d’une application. Par exemple, le fragment de code suivant déclare une variable de type <xref:System.IO.FileStream> :  
  
 [!code-vb[VbVbalrOOP#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#90)]  
  
 Étant donné que <xref:System.IO.FileStream> est un type d’objet spécifique, l’instance affectée à `FS` est à liaison anticipée.  
  
 Par opposition, un objet est dit *à liaison tardive* lorsqu’il est affecté à une variable déclarée comme étant du type `Object`. Les objets de ce type peuvent contenir des références à n’importe quel objet, mais ne présentent pas tous les avantages des objets à liaison anticipée. Par exemple, le fragment de code suivant déclare une variable objet qui contient un objet retourné par la fonction `CreateObject` :  
  
 [!code-vb[VbVbalrOOP#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/LateBinding.vb#91)]  
  
## <a name="advantages-of-early-binding"></a>Avantages de la liaison anticipée  
 Utilisez des objets à liaison anticipée chaque fois que c’est possible, car ils permettent au compilateur d’effectuer d’importantes optimisations qui génèrent des applications plus efficaces. Les objets à liaison anticipée sont considérablement plus rapides que les objets à liaison tardive et rendent votre code plus facile à lire et à gérer en indiquant exactement quels types d’objets sont utilisés. L’un des avantages de la liaison précoce est qu’elle permet des fonctionnalités utiles telles que la saisie semi-automatique du code et l’aide dynamique, car l’environnement de développement intégré (IDE) de Visual Studio peut déterminer exactement le type d’objet avec lequel vous travaillez lorsque vous modifiez le code. Elle réduit le nombre et la gravité des erreurs d’exécution, car elle permet au compilateur de signaler des erreurs à la compilation du programme.  
  
> [!NOTE]
> La liaison tardive ne peut être utilisée que pour accéder aux membres de type déclarés comme `Public`. L’accès aux membres déclarés comme `Friend` ou `Protected Friend` provoque une erreur d’exécution.  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>
- [Durée de vie d’un objet : création et destruction des objets](../objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Object Data Type](../../../language-reference/data-types/object-data-type.md)
