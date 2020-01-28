---
title: DomainUpDown, contrôle
ms.date: 03/30/2017
helpviewer_keywords:
- DomainUpDown control [Windows Forms]
- spin button control [Windows Forms], up-down controls
- up-down controls
- spin button control
- up-down controls [Windows Forms], spin button controls
ms.assetid: fb7cf017-e931-4a95-9d21-8caee4ee122a
ms.openlocfilehash: b538350a84e341d6b2759a7db28f8799f3777a86
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745828"
---
# <a name="domainupdown-control-windows-forms"></a>DomainUpDown, contrôle (Windows Forms)
Le contrôle Windows Forms <xref:System.Windows.Forms.DomainUpDown> ressemble à une combinaison d’une zone de texte et d’une paire de boutons pour déplacer vers le haut ou vers le haut dans une liste. Le contrôle affiche et définit une chaîne de texte à partir d’une liste de choix. L’utilisateur peut sélectionner la chaîne en cliquant sur les boutons haut et bas pour parcourir une liste, en appuyant sur les touches de direction haut et bas, ou en tapant une chaîne qui correspond à un élément de la liste. Une utilisation possible de ce contrôle consiste à sélectionner des éléments dans une liste de noms triée par ordre alphabétique. (Pour trier la liste, affectez à la propriété <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> la valeur `true`.) La fonction de ce contrôle est très similaire à la zone de liste ou à la zone de liste déroulante, mais elle occupe très peu d’espace.  
  
 Les propriétés de clé du contrôle sont <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>et <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>. La propriété <xref:System.Windows.Forms.DomainUpDown.Items%2A> contient la liste des objets dont les valeurs de texte sont affichées dans le contrôle. Si <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> est défini sur `false`, le contrôle complète automatiquement le texte que l’utilisateur tape et le met en correspondance avec une valeur de la liste. Si <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> est défini sur `true`, le fait de faire défiler le dernier élément vous permet d’accéder au premier élément de la liste et vice versa. Les principales méthodes du contrôle sont <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> et <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.  
  
 Ce contrôle affiche uniquement les chaînes de texte. Si vous souhaitez un contrôle qui affiche des valeurs numériques, utilisez le contrôle <xref:System.Windows.Forms.NumericUpDown>. Pour plus d’informations, consultez [contrôle NumericUpDown](numericupdown-control-windows-forms.md) .  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble du contrôle DomainUpDown](domainupdown-control-overview-windows-forms.md)  
 Présente les concepts généraux du contrôle <xref:System.Windows.Forms.DomainUpDown>, qui permet aux utilisateurs de parcourir et de sélectionner à partir d’une liste de chaînes de texte.  
  
 [Guide pratique pour ajouter par programme des éléments aux contrôles DomainUpDown Windows Forms](how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md)  
 Décrit comment spécifier les chaînes de texte que le contrôle <xref:System.Windows.Forms.DomainUpDown> doit afficher.  
  
 [Guide pratique pour supprimer des éléments des contrôles DomainUpDown Windows Forms](how-to-remove-items-from-windows-forms-domainupdown-controls.md)  
 Décrit comment supprimer des éléments du contrôle <xref:System.Windows.Forms.DomainUpDown> dans le code.  
  
## <a name="reference"></a>Reference  
 <xref:System.Windows.Forms.DomainUpDown>  
 Décrit cette classe et fournit des liens vers tous ses membres.  
  
 <xref:System.Windows.Forms.NumericUpDown>  
 Décrit cette classe et contient des liens vers tous ses membres.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)  
 Fournit une liste complète de contrôles Windows Forms, avec des liens vers des informations sur leur utilisation.
