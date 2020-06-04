---
title: RaiseEvent, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
helpviewer_keywords:
- raising events [Visual Basic], RaiseEvent statement
- RaiseEvent statement [Visual Basic]
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
ms.openlocfilehash: 46b93c060a12d82b34dafdf3aa4ea677df6f54cd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404289"
---
# <a name="raiseevent-statement"></a>RaiseEvent, instruction
Déclenche un événement déclaré au niveau du module au sein d’une classe, d’un formulaire ou d’un document.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a>Éléments  
 `eventname`  
 Obligatoire. Nom de l’événement à déclencher.  
  
 `argumentlist`  
 Facultatif. Liste de variables, de tableaux ou d’expressions délimitée par des virgules. L' `argumentlist` argument doit être placé entre parenthèses. S’il n’y a pas d’arguments, les parenthèses doivent être omises.  
  
## <a name="remarks"></a>Notes  
 Le requis `eventname` est le nom d’un événement déclaré dans le module. Il suit Visual Basic conventions d’affectation des noms de variables.  
  
 Si l’événement n’a pas été déclaré dans le module dans lequel il est déclenché, une erreur se produit. Le fragment de code suivant illustre une déclaration d’événement et une procédure dans laquelle l’événement est déclenché.  
  
 [!code-vb[VbVbalrEvents#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#37)]  
  
 Vous ne pouvez pas utiliser `RaiseEvent` pour déclencher des événements qui ne sont pas explicitement déclarés dans le module. Par exemple, tous les formulaires héritent d’un <xref:System.Windows.Forms.Control.Click> événement de <xref:System.Windows.Forms.Form?displayProperty=nameWithType> , il ne peut pas être déclenché à l’aide `RaiseEvent` de dans un formulaire dérivé. Si vous déclarez un `Click` événement dans le module de formulaire, il occulte le propre événement du formulaire <xref:System.Windows.Forms.Control.Click> . Vous pouvez toujours appeler l’événement du formulaire <xref:System.Windows.Forms.Control.Click> en appelant la <xref:System.Windows.Forms.Control.OnClick%2A> méthode.  
  
 Par défaut, un événement défini dans Visual Basic déclenche ses gestionnaires d’événements dans l’ordre dans lequel les connexions sont établies. Étant donné que les événements peuvent avoir des `ByRef` paramètres, un processus qui se connecte tardivement peut recevoir des paramètres qui ont été modifiés par un gestionnaire d’événements antérieur. Une fois que les gestionnaires d’événements s’exécutent, le contrôle est retourné à la sous-routine qui a déclenché l’événement.  
  
> [!NOTE]
> Les événements non partagés ne doivent pas être déclenchés dans le constructeur de la classe dans laquelle ils sont déclarés. Bien que ces événements ne provoquent pas d’erreurs d’exécution, ils peuvent ne pas être détectés par les gestionnaires d’événements associés. Utilisez le `Shared` modificateur pour créer un événement partagé si vous devez déclencher un événement à partir d’un constructeur.  
  
> [!NOTE]
> Vous pouvez modifier le comportement par défaut des événements en définissant un événement personnalisé. Pour les événements personnalisés, l' `RaiseEvent` instruction appelle l’accesseur de l’événement `RaiseEvent` . Pour plus d’informations sur les événements personnalisés, consultez [Event Statement](event-statement.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise des événements pour décompter les secondes de 10 à 0. Le code illustre plusieurs méthodes, propriétés et instructions liées aux événements, y compris l' `RaiseEvent` instruction.  
  
 La classe qui déclenche un événement est la source de l'événement, et les méthodes qui traitent l'événement sont les gestionnaires d'événements. Une source d'événement peut avoir plusieurs gestionnaires pour les événements qu'elle génère. Quand la classe déclenche l'événement, celui-ci se produit pour chaque classe ayant choisi de gérer les événements pour cette instance de l'objet.  
  
 L'exemple utilise également un formulaire (`Form1`) avec un bouton (`Button1`) et une zone de texte (`TextBox1`). Quand vous cliquez sur le bouton, la première zone de texte affiche un compte à rebours de 10 à 0 secondes. Quand la durée totale (10 secondes) s'est écoulée, la première zone de texte affiche « Terminé ».  
  
 Le code correspondant à `Form1` indique les états de début et de fin du formulaire. Il contient également le code exécuté lors du déclenchement des événements.  
  
 Pour utiliser cet exemple, ouvrez un nouveau projet d’application Windows, ajoutez un bouton nommé `Button1` et une zone de texte nommée `TextBox1` au formulaire principal, nommé `Form1` . Cliquez ensuite avec le bouton droit sur le formulaire, puis cliquez sur **afficher le code** pour ouvrir l’éditeur de code.  
  
 Ajoutez une `WithEvents` variable à la section declarations de la `Form1` classe.  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
## <a name="example"></a>Exemple  
 Ajoutez le code suivant au code pour `Form1`. Remplacez toutes les procédures en double qui peuvent exister, telles que `Form_Load` , ou `Button_Click` .  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 Appuyez sur F5 pour exécuter l’exemple précédent, puis cliquez sur le bouton **Démarrer**. La première zone de texte commence à décompter les secondes. Quand la durée totale (10 secondes) s'est écoulée, la première zone de texte affiche « Terminé ».  
  
> [!NOTE]
> La `My.Application.DoEvents` méthode ne traite pas les événements exactement de la même façon que le formulaire. Pour permettre au formulaire de gérer directement les événements, vous pouvez utiliser le multithreading. Pour plus d’informations, consultez [threads managés](../../../standard/threading/index.md).  
  
## <a name="see-also"></a>Voir aussi

- [Événements](../../programming-guide/language-features/events/index.md)
- [Event, instruction](event-statement.md)
- [AddHandler, instruction](addhandler-statement.md)
- [RemoveHandler, instruction](removehandler-statement.md)
- [Poignées](handles-clause.md)
