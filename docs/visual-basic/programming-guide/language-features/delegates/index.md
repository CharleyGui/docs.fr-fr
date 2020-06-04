---
title: Délégués
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [Visual Basic]
- Visual Basic code, delegates
ms.assetid: 410b60dc-5e60-4ec0-bfae-426755a2ee28
ms.openlocfilehash: 1f161248fa04f8fab0e5335413e69ca565732f71
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410681"
---
# <a name="delegates-visual-basic"></a>Délégués (Visual Basic)

Les délégués sont des objets qui font référence à des méthodes. Ils sont parfois décrits comme des *pointeurs de fonction de type sécurisé*, car ils sont comparables aux pointeurs de fonction utilisés dans d’autres langages de programmation. Mais contrairement aux pointeurs de fonction, les délégués Visual Basic sont un type référence basé sur la classe <xref:System.Delegate?displayProperty=nameWithType> . Les délégués peuvent faire référence à des méthodes partagées (méthodes qui peuvent être appelées sans une instance spécifique de classe) et des méthodes d’instance.

## <a name="delegates-and-events"></a>Délégués et événements

Les délégués sont utiles dans les situations où un intermédiaire est nécessaire entre une procédure appelante et la procédure appelée. Par exemple, vous pouvez créer un objet qui déclenche des événements pour pouvoir appeler différents gestionnaires d’événements dans différentes circonstances. Malheureusement, l’objet qui déclenche les événements ne peut pas savoir à l’avance quel gestionnaire d’événements gère un événement donné. Visual Basic vous permet d’associer de manière dynamique des gestionnaires d’événements à des événements en créant un délégué pour vous lorsque vous utilisez l' `AddHandler` instruction. À l’exécution, le délégué transmet les appels au gestionnaire d’événements approprié.

Bien que vous puissiez créer vos propres délégués, dans la plupart des cas Visual Basic crée le délégué et s’occupe des détails pour vous. Par exemple, une instruction `Event` définit implicitement une classe déléguée nommée `<EventName>EventHandler` comme classe imbriquée de la classe contenant l’instruction `Event`, avec la même signature que l’événement. L’instruction `AddressOf` crée implicitement une instance d’un délégué qui fait référence à une procédure spécifique. Les deux lignes de code suivantes sont équivalentes. Dans la première ligne, vous voyez la création explicite d’une instance de `EventHandler`, avec une référence à la méthode `Button1_Click` envoyée comme argument. La deuxième ligne est un moyen plus commode de faire la même chose.

[!code-vb[VbVbalrDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#6)]

Vous pouvez utiliser la syntaxe raccourcie pour créer des délégués dès l’instant où le compilateur peut déterminer le type du délégué par le contexte.

## <a name="declaring-events-that-use-an-existing-delegate-type"></a>Déclaration d’événements utilisant un type délégué existant

Dans certaines situations, vous souhaiterez peut-être déclarer un événement pour utiliser un type délégué existant comme son délégué sous-jacent. La syntaxe suivante montre comment :

[!code-vb[VbVbalrDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#7)]

C’est utile pour acheminer plusieurs événements vers le même gestionnaire.

## <a name="delegate-variables-and-parameters"></a>Paramètres et variables délégués

Vous pouvez utiliser des délégués pour d’autres tâches non liées aux événements, telles que le threading libre, ou avec des procédures qui doivent appeler différentes versions de fonctions à l’exécution.

Par exemple, supposons que vous disposez d’une application de petites annonces qui comprend une zone de liste avec les noms de voitures. Les annonces sont triées par titre, qui correspond normalement à la marque de la voiture. Vous pouvez rencontrer le cas de figure où certaines voitures indiquent l’année de la voiture avant la marque. Le problème est que la fonctionnalité de tri prédéfinie de la zone de liste trie seulement par code de caractères ; elle place en premier toutes les annonces qui commencent par une date, suivies des annonces qui commencent par la marque.

Pour résoudre ce problème, vous pouvez créer une procédure de tri dans une classe qui utilise le tri alphabétique standard sur la plupart des zones de liste, mais qui est capable, à l’exécution, de passer à la procédure de tri personnalisé pour les annonces de voiture. Pour ce faire, transmettez la procédure de tri personnalisée à la classe de tri à l’exécution, à l’aide de délégués.

## <a name="addressof-and-lambda-expressions"></a>Expressions lambda et AddressOf

Chaque classe déléguée définit un constructeur auquel les caractéristiques d’une méthode objet sont passées. L’argument d’un constructeur délégué doit être une référence à une méthode ou une expression lambda.

Pour spécifier une référence à une méthode, utilisez la syntaxe suivante :

`AddressOf` [`expression`.]`methodName`

Le type de compilation de `expression` doit être le nom d’une classe ou d’une interface qui contient une méthode portant le nom spécifié, dont la signature corresponde à celle de la classe déléguée. La méthode `methodName` peut être une méthode partagée ou d’instance. `methodName` n’est pas facultatif, même si l’on crée un délégué pour la méthode par défaut de la classe.

Pour spécifier une expression lambda, utilisez la syntaxe suivante :

`Function` ([`parm` As `type`, `parm2` As `type2`, ...]) `expression`

L’exemple suivant illustre les expressions lambda et `AddressOf` utilisées pour spécifier la référence d’un délégué.

[!code-vb[VbVbalrDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class2.vb#15)]

La signature de la fonction doit correspondre à celle du type délégué. Pour plus d’informations sur les expressions lambda, consultez [expressions lambda](../procedures/lambda-expressions.md). Pour voir plus d’exemples d’affectation d’expressions lambda et `AddressOf` aux délégués, consultez la page [Conversion souple des délégués](relaxed-delegate-conversion.md).

## <a name="related-topics"></a>Rubriques connexes

|Intitulé|Description|
|-----------|-----------------|
|[Comment : appeler une méthode déléguée](how-to-invoke-a-delegate-method.md)|Fournit un exemple d’association d’une méthode à un délégué, puis d’appel de cette méthode par le biais du délégué.|
|[Comment : passer des procédures à une autre procédure en Visual Basic](how-to-pass-procedures-to-another-procedure.md)|Montre comment utiliser des délégués pour transmettre une procédure à une autre procédure.|
|[Conversion simplifiée des délégués](relaxed-delegate-conversion.md)|Explique comment affecter des sous-routines et des fonctions aux délégués ou aux gestionnaires même si leurs signatures ne sont pas identiques.|
|[Événements](../events/index.md)|Fournit une vue d’ensemble des événements en Visual Basic.|
