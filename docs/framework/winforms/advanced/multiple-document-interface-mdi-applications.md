---
title: Applications d'interface multidocument (MDI, Multiple Document Interface)
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 23e0275d5e6b081ec02d669a78e8695453360637
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956557"
---
# <a name="multiple-document-interface-mdi-applications"></a>Applications d'interface multidocument (MDI, Multiple Document Interface)
Les applications d’interface multidocument (MDI, multiple-document interface) vous permettent d’afficher plusieurs documents en même temps, chaque document étant affiché dans sa propre fenêtre. Les applications MDI ont souvent un élément de menu fenêtre avec des sous-menus pour basculer entre les fenêtres ou les documents.  
  
> [!NOTE]
> Il existe des différences de comportement entre les formulaires MDI et les fenêtres SDI (single-document interface) dans Windows Forms. La `Opacity` propriété n’affecte pas l’apparence des formulaires enfants MDI. En outre, la <xref:System.Windows.Forms.Form.CenterToParent%2A> méthode n’affecte pas le comportement des formulaires enfants MDI.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour Créer des formulaires MDI parents](how-to-create-mdi-parent-forms.md)  
 Explique comment créer le conteneur pour les documents multiples dans une application MDI.  
  
 [Guide pratique pour Créer des formulaires MDI enfants](how-to-create-mdi-child-forms.md)  
 Explique comment créer une ou plusieurs fenêtres qui fonctionnent dans un formulaire MDI parent.  
  
 [Guide pratique pour Déterminer l’enfant MDI actif](how-to-determine-the-active-mdi-child.md)  
 Fournit des instructions pour vérifier la fenêtre enfant qui a le focus (et envoyer son contenu vers le presse-papiers).  
  
 [Guide pratique pour Envoyer des données à l’enfant MDI actif](how-to-send-data-to-the-active-mdi-child.md)  
 Explique comment transporter des informations vers la fenêtre enfant active.  
  
 [Guide pratique pour Réorganiser les formulaires enfants MDI](how-to-arrange-mdi-child-forms.md)  
 Fournit des instructions pour la mosaïque, la cascade ou la réorganisation des fenêtres enfants d’une application MDI.
