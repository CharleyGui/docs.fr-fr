---
title: Vue d'ensemble des graphismes
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
ms.openlocfilehash: f0e2fd9dcf31e5fdce16b5a3b6fd21eab6eab66a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505325"
---
# <a name="overview-of-graphics"></a>Vue d'ensemble des graphismes
GDI + est une interface de programmation d’application (API) qui forme le sous-système du système d’exploitation Microsoft Windows. GDI + est responsable de l’affichage des informations sur les écrans et les imprimantes. Comme son nom l’indique, GDI + est le successeur de GDI, l’Interface graphique inclus avec les versions antérieures de Windows.  
  
## <a name="managed-class-interface"></a>Interface de classes managées  
 L’API GDI + est exposée via un ensemble de classes déployées comme du code managé. Cet ensemble de classes est appelé le *interface de classes managées* à GDI +. Les espaces de noms suivants composent l'interface de classes managées :  
  
- <xref:System.Drawing>  
  
- <xref:System.Drawing.Drawing2D>  
  
- <xref:System.Drawing.Imaging>  
  
- <xref:System.Drawing.Text>  
  
- <xref:System.Drawing.Printing>  
  
 Avec une Interface graphique, tels que GDI +, vous pouvez afficher des informations sur un écran ou une imprimante sans avoir à se soucier des détails d’un périphérique d’affichage particulier. Le programmeur effectue des appels aux méthodes fournies par les classes de GDI +. Ces méthodes effectuent ensuite les appels appropriés aux pilotes de périphériques spécifiques. GDI + isole l’application du matériel graphique. C’est cette isolation qui permet à un programmeur créer des applications indépendantes du périphérique.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des graphismes](graphics-overview-windows-forms.md)
