---
title: Vue d'ensemble du contrôle DomainUpDown (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
ms.openlocfilehash: 6fda542204e2b41dd1d729d2b940c6f38a5812ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965298"
---
# <a name="domainupdown-control-overview-windows-forms"></a>Vue d'ensemble du contrôle DomainUpDown (Windows Forms)
Le contrôle <xref:System.Windows.Forms.DomainUpDown> Windows Forms est essentiellement une combinaison d’une zone de texte et d’une paire de boutons pour déplacer vers le haut ou vers le haut dans une liste. Le contrôle affiche et définit une chaîne de texte à partir d’une liste de choix. L’utilisateur peut sélectionner la chaîne en cliquant sur les boutons haut et bas pour parcourir une liste, en appuyant sur les touches de direction haut et bas, ou en tapant une chaîne qui correspond à un élément de la liste. Une utilisation possible de ce contrôle consiste à sélectionner des éléments dans une liste de noms triée par ordre alphabétique.  
  
> [!NOTE]
> Pour trier la liste, affectez <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> à `true`la propriété la valeur.  
  
 La fonction de ce contrôle est très similaire à la zone de liste ou à la zone de liste déroulante, mais elle occupe très peu d’espace.  
  
## <a name="key-properties"></a>Propriétés de clé  
 Les propriétés de clé du contrôle sont <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>et <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>. La <xref:System.Windows.Forms.DomainUpDown.Items%2A> propriété contient la liste des objets dont les valeurs de texte sont affichées dans le contrôle. Si <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> a la `false`valeur, le contrôle termine automatiquement le texte que l’utilisateur tape et le met en correspondance avec une valeur de la liste. Si <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> a la `true`valeur, le défilement au-delà du dernier élément vous permet d’accéder au premier élément de la liste et vice versa. Les méthodes clés du contrôle sont <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> et. <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>  
  
 Ce contrôle affiche uniquement les chaînes de texte. Si vous souhaitez un contrôle qui affiche des valeurs numériques, utilisez <xref:System.Windows.Forms.NumericUpDown> le contrôle. Pour plus d’informations, consultez [vue d’ensemble du contrôle NumericUpDown](numericupdown-control-overview-windows-forms.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DomainUpDown>
- [DomainUpDown, contrôle](domainupdown-control-windows-forms.md)
