---
title: Applications d'interface multidocument (MDI, Multiple Document Interface)
description: Découvrez comment Windows Forms des applications d’interface multidocument (MDI) vous permettent d’afficher plusieurs documents en même temps, chaque document étant affiché dans sa propre fenêtre.
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 0912a989ac1710d72c9db1cceb0e695f0ca85dee
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174651"
---
# <a name="multiple-document-interface-mdi-applications"></a>Applications d'interface multidocument (MDI, Multiple Document Interface)
Les applications d’interface multidocument (MDI, multiple-document interface) vous permettent d’afficher plusieurs documents en même temps, chaque document étant affiché dans sa propre fenêtre. Les applications MDI ont souvent un élément de menu fenêtre avec des sous-menus pour basculer entre les fenêtres ou les documents.  
  
> [!NOTE]
> Il existe des différences de comportement entre les formulaires MDI et les fenêtres SDI (single-document interface) dans Windows Forms. La `Opacity` propriété n’affecte pas l’apparence des formulaires enfants MDI. En outre, la <xref:System.Windows.Forms.Form.CenterToParent%2A> méthode n’affecte pas le comportement des formulaires enfants MDI.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour créer des formulaires MDI parents](how-to-create-mdi-parent-forms.md)  
 Explique comment créer le conteneur pour les documents multiples dans une application MDI.  
  
 [Comment : créer des formulaires MDI enfants](how-to-create-mdi-child-forms.md)  
 Explique comment créer une ou plusieurs fenêtres qui fonctionnent dans un formulaire MDI parent.  
  
 [Comment : déterminer l'enfant MDI actif](how-to-determine-the-active-mdi-child.md)  
 Fournit des instructions pour vérifier la fenêtre enfant qui a le focus (et envoyer son contenu vers le presse-papiers).  
  
 [Comment : envoyer des données à l'enfant MDI actif](how-to-send-data-to-the-active-mdi-child.md)  
 Explique comment transporter des informations vers la fenêtre enfant active.  
  
 [Guide pratique pour réorganiser des formulaires MDI enfants](how-to-arrange-mdi-child-forms.md)  
 Fournit des instructions pour la mosaïque, la cascade ou la réorganisation des fenêtres enfants d’une application MDI.
