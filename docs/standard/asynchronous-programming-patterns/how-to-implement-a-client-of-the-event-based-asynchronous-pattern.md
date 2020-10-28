---
title: 'Procédure : implémenter un client du modèle asynchrone basé sur des événements'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET], asynchronous features
- components [.NET], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 21a858c1-3c99-4904-86ee-0d17b49804fa
ms.openlocfilehash: 95997f219a08c131905cfc86b78e94c36f3ec851
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888813"
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a>Procédure : implémenter un client du modèle asynchrone basé sur des événements
L’exemple de code suivant montre comment utiliser un composant conforme à la [vue d'ensemble du modèle asynchrone basé sur des événements](event-based-asynchronous-pattern-overview.md). Le formulaire de cet exemple utilise le composant `PrimeNumberCalculator` décrit dans la rubrique [Comment : implémenter un composant qui prend en charge le modèle asynchrone basé sur des événements](component-that-supports-the-event-based-asynchronous-pattern.md).  
  
 Quand vous exécutez un projet utilisant cet exemple, un formulaire « Calculatrice de nombres premiers » s’affiche avec une grille et deux boutons : **Démarrer une nouvelle tâche** et **Annuler** . Si vous cliquez plusieurs fois de suite sur le bouton **Démarrer une nouvelle tâche** , à chaque clic, une opération asynchrone lance un calcul pour déterminer si un nombre test généré de manière aléatoire est un nombre premier. Le formulaire affiche régulièrement la progression et des résultats incrémentiels. Chaque opération est assignée à un ID de tâche unique. Le résultat du calcul est affiché dans la colonne **Résultat** . Si le nombre test n’est pas un nombre premier, il est étiqueté en tant que **Composite** et son premier diviseur est affiché.  
  
 Toute opération en attente peut être annulée à l’aide du bouton **Annuler** . Il est possible d’effectuer des sélections multiples.  
  
> [!NOTE]
> La plupart des nombres ne seront pas des nombres premiers. Si aucun nombre premier n’a été trouvé après plusieurs opérations, démarrez simplement davantage de tâches jusqu’à trouver des nombres premiers.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ComponentModel.AsyncOperation>
- <xref:System.ComponentModel.AsyncOperationManager>
- <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
