---
title: Fonctionnalités par défaut du contrôle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
ms.openlocfilehash: b695883ac7ec3fb0c459adb66214b0eceab3a128
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746132"
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a>Fonctionnalités par défaut du contrôle DataGridView Windows Forms
Le contrôle Windows Forms <xref:System.Windows.Forms.DataGridView> fournit aux utilisateurs une quantité significative de fonctionnalités par défaut.  
  
## <a name="default-functionality"></a>Fonctionnalité par défaut  
 Par défaut, un contrôle de <xref:System.Windows.Forms.DataGridView> :  
  
- Affiche automatiquement les en-têtes de colonnes et les en-têtes de lignes qui restent visibles lorsque la table défile verticalement.  
  
- Possède un en-tête de ligne qui contient un indicateur de sélection pour la ligne actuelle.  
  
- Possède un rectangle de sélection dans la première cellule.  
  
- Contient des colonnes qui peuvent être redimensionnées automatiquement lorsque l’utilisateur double-clique sur les séparateurs de colonnes.  
  
- Prend automatiquement en charge les styles visuels sur Windows XP et la famille Windows Server 2003 quand la méthode <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> est appelée à partir de la méthode `Main` de l’application.  
  
 En outre, le contenu d’un contrôle de <xref:System.Windows.Forms.DataGridView> peut être modifié par défaut :  
  
- Si l’utilisateur double-clique ou appuie sur F2 dans une cellule, le contrôle met automatiquement la cellule en mode édition et met à jour le contenu de la cellule au fur et à mesure que l’utilisateur tape.  
  
- Si l’utilisateur fait défiler jusqu’à la fin de la grille, l’utilisateur verra qu’une ligne pour l’ajout de nouveaux enregistrements est présente. Quand l’utilisateur clique sur cette ligne, une nouvelle ligne est ajoutée au contrôle <xref:System.Windows.Forms.DataGridView>, avec les valeurs par défaut. Quand l’utilisateur appuie sur ÉCHAP, cette nouvelle ligne disparaît.  
  
- Si l’utilisateur clique sur un en-tête de ligne, la ligne entière est sélectionnée.  
  
 Quand vous liez un contrôle <xref:System.Windows.Forms.DataGridView> à une source de données en définissant sa propriété <xref:System.Windows.Forms.DataGridView.DataSource%2A>, le contrôle :  
  
- Utilise automatiquement les noms des colonnes de la source de données comme texte d’en-tête de colonne.  
  
- Est rempli avec le contenu de la source de données. <xref:System.Windows.Forms.DataGridView> colonnes sont automatiquement créées pour chaque colonne de la source de données.  
  
- Crée une ligne pour chaque ligne visible dans la table.  
  
- Trie automatiquement les lignes en fonction des données sous-jacentes lorsque l’utilisateur clique sur un en-tête de colonne.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- [DataGridView, contrôle](datagridview-control-windows-forms.md)
