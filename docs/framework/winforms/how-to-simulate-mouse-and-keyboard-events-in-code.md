---
title: 'Procédure : simuler des événements de souris et de clavier dans le code'
description: Découvrez comment utiliser les options Windows Forms permet de simuler par programmation les entrées de souris et de clavier.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboards [Windows Forms], event simulation
- user input [Windows Forms], simulating
- SendKeys [Windows Forms], using
- mouse clicks [Windows Forms], simulating
- mouse [Windows Forms], event simulation
ms.assetid: 6abcb67e-3766-4af2-9590-bf5dabd17e41
ms.openlocfilehash: 9b453787f7fa7f5041f75e04d65557a0a3838bee
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904362"
---
# <a name="how-to-simulate-mouse-and-keyboard-events-in-code"></a>Procédure : simuler des événements de souris et de clavier dans le code

Windows Forms fournit plusieurs options pour simuler par programmation l'entrée de souris et de clavier. Cette rubrique offre une vue d'ensemble de ces options.

## <a name="simulating-mouse-input"></a>Simulation de l'entrée de souris

Le meilleur moyen de simuler des événements de souris consiste à appeler la méthode `On`*EventName* qui déclenche l'événement de souris que vous souhaitez simuler. Cette option est généralement possible uniquement dans les contrôles et les formulaires personnalisés, car les méthodes qui déclenchent des événements sont protégées et ne sont pas accessibles en dehors du contrôle ou du formulaire. Par exemple, les étapes suivantes illustrent comment simuler un clic sur le bouton droit de la souris dans le code.

#### <a name="to-programmatically-click-the-right-mouse-button"></a>Pour cliquer sur le bouton droit de la souris par programmation

1. Créez un <xref:System.Windows.Forms.MouseEventArgs> dont la propriété <xref:System.Windows.Forms.MouseEventArgs.Button%2A> a la valeur <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType> .

2. Appelez la méthode <xref:System.Windows.Forms.Control.OnMouseClick%2A> avec ce <xref:System.Windows.Forms.MouseEventArgs> comme argument.

Pour plus d’informations sur les contrôles personnalisés, consultez [Développement de contrôles Windows Forms au moment du design](./controls/developing-windows-forms-controls-at-design-time.md).

Il existe d'autres manières de simuler l'entrée de souris. Par exemple, vous pouvez définir par programmation une propriété de contrôle qui représente un état qui est généralement défini par une entrée de souris (telle que la propriété <xref:System.Windows.Forms.CheckBox.Checked%2A> du contrôle <xref:System.Windows.Forms.CheckBox> ) ou vous pouvez appeler directement le délégué qui est attaché à l'événement que vous souhaitez simuler.

## <a name="simulating-keyboard-input"></a>Simulation de l'entrée au clavier

Bien que vous puissiez simuler l'entrée au clavier à l'aide des stratégies abordées ci-dessus pour l'entrée de souris, Windows Forms fournit également la classe <xref:System.Windows.Forms.SendKeys> pour envoyer des séquences de touches à l'application active.

> [!CAUTION]
> Si votre application est prévue pour une utilisation internationale avec différents claviers, l'utilisation de <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> peut produire des résultats imprévisibles et doit être évitée.

> [!NOTE]
> La classe <xref:System.Windows.Forms.SendKeys> a été mise à jour pour .NET Framework 3.0 pour pouvoir être utilisée dans les applications qui s'exécutent sur Windows Vista. La sécurité renforcée de Windows Vista (également appelée Contrôle de compte d'utilisateur) empêche le fonctionnement correcte de l'implémentation précédente.
>
> La classe <xref:System.Windows.Forms.SendKeys> est vulnérable aux problèmes de synchronisation, que certains développeurs ont dû contourner. L'implémentation mise à jour est toujours vulnérable aux problèmes de synchronisation, mais est légèrement plus rapide et peut nécessiter certaines modifications des solutions de contournement. La classe <xref:System.Windows.Forms.SendKeys> tente d'abord d'utiliser l'implémentation précédente et, en cas d'échec, utilise la nouvelle implémentation. Ainsi, la classe <xref:System.Windows.Forms.SendKeys> peut se comporter différemment sur différents systèmes d'exploitation. En outre, quand la classe <xref:System.Windows.Forms.SendKeys> utilise la nouvelle implémentation, la méthode <xref:System.Windows.Forms.SendKeys.SendWait%2A> n'attend pas que les messages soient traités quand ils sont envoyés à un autre processus.
>
> Si votre application repose sur un comportement cohérent indépendamment du système d'exploitation, vous pouvez forcer la classe <xref:System.Windows.Forms.SendKeys> à utiliser la nouvelle implémentation en ajoutant le paramètre d'application suivant à votre fichier app.config.
>
> ```xml
> <appSettings>
>  <add key="SendKeys" value="SendInput"/>
> </appSettings>
> ```
>
> Pour forcer la classe <xref:System.Windows.Forms.SendKeys> à utiliser l'implémentation précédente, utilisez plutôt la valeur `"JournalHook"` .

#### <a name="to-send-a-keystroke-to-the-same-application"></a>Pour envoyer une séquence de touches à la même application

1. Appelez la méthode <xref:System.Windows.Forms.SendKeys.Send%2A> ou <xref:System.Windows.Forms.SendKeys.SendWait%2A> de la classe <xref:System.Windows.Forms.SendKeys> . Les séquences de touches spécifiées seront reçues par le contrôle actif de l'application. L'exemple de code suivant utilise <xref:System.Windows.Forms.SendKeys.Send%2A> pour simuler une pression sur la touche Entrée quand l'utilisateur double-clique sur la surface du formulaire. Cet exemple suppose que l'on a un <xref:System.Windows.Forms.Form> avec un seul contrôle <xref:System.Windows.Forms.Button> ayant un index de tabulation de 0.

    [!code-cpp[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#10)]
    [!code-csharp[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#10)]
    [!code-vb[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#10)]

#### <a name="to-send-a-keystroke-to-a-different-application"></a>Pour envoyer une séquence de touches vers une autre application

1. Activez la fenêtre d'application qui recevra les séquences de touches, puis appelez la méthode <xref:System.Windows.Forms.SendKeys.Send%2A> ou <xref:System.Windows.Forms.SendKeys.SendWait%2A> . Comme il n'existe aucune méthode managée permettant d'activer une autre application, vous devez utiliser des méthodes Windows natives pour forcer le focus sur d'autres applications. L'exemple de code suivant utilise l'appel de code non managé pour appeler les méthodes `FindWindow` et `SetForegroundWindow` pour activer la fenêtre de l'application Calculatrice, puis appelle <xref:System.Windows.Forms.SendKeys.SendWait%2A> pour émettre une série de calculs vers l'application Calculatrice.

    > [!NOTE]
    > Les paramètres corrects de l'appel `FindWindow` qui recherche l'application Calculatrice varient en fonction de votre version de Windows.  Le code suivant recherche l’application Calculator sur Windows 7. Sur Windows Vista, remplacez le premier paramètre par « SciCalc ». Vous pouvez utiliser l'outil Spy++, fourni avec Visual Studio, pour déterminer les paramètres corrects.

    [!code-cpp[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#5)]
    [!code-csharp[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#5)]
    [!code-vb[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#5)]

## <a name="example"></a>Exemple

L'exemple de code suivant est l'application complète pour les exemples de code précédents.

[!code-cpp[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#0)]
[!code-csharp[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#0)]

## <a name="compiling-the-code"></a>Compilation du code

Cet exemple nécessite :

- des références aux assemblys System, System.Drawing et System.Windows.Forms.

## <a name="see-also"></a>Voir aussi

- [Entrées d'utilisateur dans les Windows Forms](user-input-in-windows-forms.md)
