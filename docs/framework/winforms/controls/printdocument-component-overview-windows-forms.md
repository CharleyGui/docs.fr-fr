---
title: Vue d'ensemble du composant PrintDocument (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: 16a7f3a34ccb280f7bf91c52e29b20edc22130b9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928991"
---
# <a name="printdocument-component-overview-windows-forms"></a>Vue d'ensemble du composant PrintDocument (Windows Forms)

Le composant [PrintDocument](printdocument-component-windows-forms.md) Windows Forms permet de définir les propriétés qui décrivent les éléments à imprimer, puis d’imprimer le document dans des applications Windows. Il peut être utilisé conjointement avec le composant [PrintDialog](printdialog-component-windows-forms.md) pour contrôler tous les aspects de l’impression du document.

## <a name="working-with-the-printdocument-component"></a>Utilisation du composant PrintDocument

Deux des principaux scénarios qui impliquent le <xref:System.Drawing.Printing.PrintDocument> composant sont les suivants:

- Travaux d’impression simples, tels que l’impression d’un fichier texte. Dans ce cas, vous devez ajouter le <xref:System.Drawing.Printing.PrintDocument> composant à un Windows Form, puis ajouter une logique de programmation qui imprime un <xref:System.Drawing.Printing.PrintDocument.PrintPage> fichier dans le gestionnaire d’événements. La logique de programmation doit se déboucher sur la <xref:System.Drawing.Printing.PrintDocument.Print%2A> méthode pour imprimer le document. Cette méthode envoie un <xref:System.Drawing.Graphics> objet, contenu dans la <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> propriété de la <xref:System.Drawing.Printing.PrintPageEventArgs> classe, à l’imprimante. Pour obtenir un exemple qui montre comment imprimer un document texte à l' <xref:System.Drawing.Printing.PrintDocument> aide du composant [, consultez Procédure: Imprimez un fichier texte contenant plusieurs pages](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)dans Windows Forms.

- Travaux d’impression plus complexes, comme lorsque vous souhaitez réutiliser la logique d’impression que vous avez écrite. Dans ce cas, vous devez dériver un nouveau composant du <xref:System.Drawing.Printing.PrintDocument> composant et remplacer (consultez [substitutions](../../../visual-basic/language-reference/modifiers/overrides.md) pour Visual Basic ou [remplacer](../../../csharp/language-reference/keywords/override.md) pour C#) l' <xref:System.Drawing.Printing.PrintDocument.PrintPage> événement.

Lorsqu’il est ajouté à un formulaire, le <xref:System.Drawing.Printing.PrintDocument> composant apparaît dans la barre d’État en bas de la Concepteur Windows Forms dans Visual Studio.

## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [Prise en charge de l’impression dans les Windows Forms](../advanced/windows-forms-print-support.md)
- [Composant PrintDocument](printdocument-component-windows-forms.md)
