---
title: 'Procédure : prendre en charge COM Interop en affichant chaque formulaire Windows sur son propre thread'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
ms.openlocfilehash: 41af4d81995a0a4eac912ecce7dc70cf04f012cd
ms.sourcegitcommit: 1e72e2990220b3635cebc39586828af9deb72d8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71306379"
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a>Procédure : Prendre en charge les COM Interop en affichant chaque Windows Form sur son propre thread

Vous pouvez résoudre les problèmes d’interopérabilité COM en affichant votre formulaire sur une boucle de messages .NET Framework, que vous pouvez créer <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> à l’aide de la méthode.

Pour qu'un Windows Form fonctionne correctement à partir d'une application cliente COM, vous devez l'exécuter sur une boucle de message Windows Forms. Pour cela, utilisez l'une des approches suivantes :

- Utilisez la méthode <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> pour afficher le Windows Form. Pour plus d'informations, voir [Procédure : Prenez en charge COM Interop en affichant un Windows Form avec la](com-interop-by-displaying-a-windows-form-shadow.md)méthode ShowDialog.

- Affichez chaque Windows Form sur un thread séparé.

Il existe une prise en charge étendue de cette fonctionnalité dans Visual Studio.

Consultez [également la procédure pas à pas: Prise en charge de COM Interop en affichant chaque Windows Form sur](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100))son propre thread.

## <a name="example"></a>Exemple

L'exemple de code suivant montre comment afficher le formulaire sur un thread distinct et appeler la méthode <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> pour démarrer une pompe de messages Windows Forms sur ce thread. Pour utiliser cette approche, vous devez marshaler tous les appels au formulaire à partir de l'application non managée à l'aide de la méthode <xref:System.Windows.Forms.Control.Invoke%2A> .

Cette approche exige que chaque instance d'un formulaire s'exécute sur son propre thread à l'aide de sa propre boucle de message. Une seule boucle de message peut s'exécuter par thread. Ainsi, vous ne pouvez pas modifier la boucle de message de l'application cliente. Toutefois, vous pouvez modifier le composant .NET Framework pour démarrer un nouveau thread qui utilise sa propre boucle de message.

[!code-vb[System.Windows.Forms.ComInterop#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]

[!code-vb[System.Windows.Forms.ComInterop#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]

[!code-vb[System.Windows.Forms.ComInterop#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]

## <a name="compile-the-code"></a>Compiler le code

Compilez le types `COMForm`, `Form1`et `FormManager` dans un assembly nommé `COMWinform.dll`. Inscrivez l’assembly pour COM Interop en utilisant l’une des méthodes décrites dans [Packaging an Assembly for COM](../../interop/packaging-an-assembly-for-com.md). Vous pouvez maintenant utiliser l'assembly et son fichier de bibliothèque de types (.tlb) correspondant dans des applications non managées. Par exemple, vous pouvez utiliser la bibliothèque de types comme référence dans un projet exécutable Visual Basic 6.0.

## <a name="see-also"></a>Voir aussi

- [Exposition de composants .NET Framework à COM](../../interop/exposing-dotnet-components-to-com.md)
- [Empaquetage d'un assembly pour COM](../../interop/packaging-an-assembly-for-com.md)
- [Inscription d’assemblys dans COM](../../interop/registering-assemblies-with-com.md)
- [Guide pratique pour Prendre en charge COM Interop en affichant un Windows Form avec la méthode ShowDialog](com-interop-by-displaying-a-windows-form-shadow.md)
- [Vue d'ensemble des applications Windows Forms et non managées](windows-forms-and-unmanaged-applications-overview.md)
