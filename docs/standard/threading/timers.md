---
title: Minuteries
description: Découvrez les minuteurs .NET à utiliser dans un environnement multithread.
ms.date: 07/03/2018
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
author: pkulikov
ms.openlocfilehash: 1ab612bc32a84c1248d311b0603a01a32a25199f
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826103"
---
# <a name="timers"></a>Minuteries

.NET propose deux minuteurs à utiliser dans un environnement multithread :

- <xref:System.Threading.Timer?displayProperty=nameWithType>, qui exécute une méthode de rappel unique sur un thread <xref:System.Threading.ThreadPool> à intervalles réguliers.
- <xref:System.Timers.Timer?displayProperty=nameWithType> qui, par défaut, déclenche un événement sur un thread <xref:System.Threading.ThreadPool> à intervalles réguliers.

> [!NOTE]
> Certaines implémentations .NET peuvent inclure des minuteurs supplémentaires :
>
> - <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> : composant Windows Forms qui déclenche un événement à intervalles réguliers. Le composant ne possède pas d’interface utilisateur et est conçu pour une utilisation dans un environnement à thread unique.  
> - <xref:System.Web.UI.Timer?displayProperty=nameWithType> : composant ASP.NET qui effectue des publications (postback) de pages web asynchrones ou synchrones à intervalles réguliers.
> - <xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType> : minuteur intégré à la file d’attente <xref:System.Windows.Threading.Dispatcher> qui est traitée selon un intervalle de temps et une priorité spécifiés.

## <a name="the-systemthreadingtimer-class"></a>Classe System.Threading.Timer

La classe <xref:System.Threading.Timer?displayProperty=nameWithType> vous permet d’appeler en permanence un délégué à des intervalles de temps spécifiés. Vous pouvez également utiliser cette classe pour planifier un appel unique à un délégué dans un intervalle de temps spécifié. Le délégué est exécuté sur un thread <xref:System.Threading.ThreadPool>.

Quand vous créez un objet <xref:System.Threading.Timer?displayProperty=nameWithType>, vous spécifiez un délégué <xref:System.Threading.TimerCallback> qui définit la méthode de rappel, un objet d’état facultatif qui est passé au rappel, la durée d’attente avant la première invocation du rappel et l’intervalle de temps entre les invocations de rappel. Pour annuler un minuteur en attente, appelez la méthode <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType>.

L’exemple suivant crée un minuteur qui appelle le délégué fourni au bout d’une seconde (1000 millisecondes) la première fois et ensuite toutes les deux secondes. L’objet d’état de l’exemple sert à compter le nombre de fois que le délégué est appelé. Le minuteur s’arrête dès que le délégué a été appelé au moins 10 fois.

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

Pour plus d’informations et d’exemples, consultez <xref:System.Threading.Timer?displayProperty=nameWithType>.

## <a name="the-systemtimerstimer-class"></a>Classe System.Timers.Timer

L’autre minuteur qui peut être utilisé dans un environnement multithread est <xref:System.Timers.Timer?displayProperty=nameWithType> qui, par défaut, déclenche un événement sur un thread <xref:System.Threading.ThreadPool>.

Au moment de créer un objet <xref:System.Timers.Timer?displayProperty=nameWithType>, vous pouvez spécifier l’intervalle de temps au cours duquel un événement <xref:System.Timers.Timer.Elapsed> est déclenché. Utilisez la propriété <xref:System.Timers.Timer.Enabled%2A> pour indiquer si un minuteur doit déclencher un événement <xref:System.Timers.Timer.Elapsed>. Si vous avez besoin qu’un événement <xref:System.Timers.Timer.Elapsed> soit déclenché une seule fois à l’issue de l’intervalle spécifié, définissez le <xref:System.Timers.Timer.AutoReset%2A> sur `false`. La valeur par défaut de la propriété <xref:System.Timers.Timer.AutoReset%2A> est `true`, ce qui signifie qu’un événement <xref:System.Timers.Timer.Elapsed> est déclenché régulièrement selon l’intervalle défini par la propriété <xref:System.Timers.Timer.Interval%2A>.

Pour plus d’informations et d’exemples, consultez <xref:System.Timers.Timer?displayProperty=nameWithType>.
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.Timer?displayProperty=nameWithType>
- <xref:System.Timers.Timer?displayProperty=nameWithType>
- [Fonctionnalités et objets de threading](threading-objects-and-features.md)
