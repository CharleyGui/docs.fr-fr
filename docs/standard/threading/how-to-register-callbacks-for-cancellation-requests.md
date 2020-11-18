---
title: Enregistrer les rappels pour les demandes d’annulation
ms.date: 08/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
ms.openlocfilehash: f551055fc6e5e4565329201e9e0be6e4a83487a1
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826402"
---
# <a name="register-callbacks-for-cancellation-requests"></a>Enregistrer les rappels pour les demandes d’annulation

Découvrez comment inscrire un délégué qui sera appelé quand une <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> propriété prend la valeur true. La valeur passe de false à true lorsqu’un appel à <xref:System.Threading.CancellationTokenSource.Cancel%2A> sur l’objet qui a créé le jeton est effectué. Utilisez cette technique pour annuler des opérations asynchrones qui ne prennent pas en charge l’infrastructure d’annulation unifiée en mode natif et pour débloquer des méthodes qui peuvent attendre la fin d’une opération asynchrone.

> [!NOTE]
> Quand l'option Uniquement mon code est activée, Visual Studio, dans certains cas, peut s'arrêter sur la ligne qui lève l'exception et afficher un message d'erreur indiquant que l'exception n'est pas gérée par le code utilisateur. Cette erreur est sans gravité. Vous pouvez appuyer sur <kbd>F5</kbd> pour continuer et voir le comportement de gestion des exceptions qui est illustré dans les exemples ci-dessous. Pour empêcher Visual Studio de s'arrêter sur la première erreur, il suffit de désactiver la case à cocher Uniquement mon code sous **Outils, Options, Débogage, Général**.

## <a name="example"></a>Exemple

Dans l'exemple suivant, la méthode <xref:System.Net.WebClient.CancelAsync%2A> est enregistrée comme la méthode à appeler quand une annulation est demandée via le jeton d'annulation.

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb":::

Si l'annulation a déjà été demandée quand le rappel est enregistré, le rappel sera malgré tout appelé. Dans ce cas particulier, la méthode <xref:System.Net.WebClient.CancelAsync%2A> ne fera rien si aucune opération asynchrone n'est en cours. Il est donc sans risque d'appeler la méthode.

## <a name="see-also"></a>Voir aussi

- [Annulation dans les threads managés](cancellation-in-managed-threads.md)
- <xref:System.Net.WebClient.DownloadStringTaskAsync(System.String)?displayProperty=nameWithType>
