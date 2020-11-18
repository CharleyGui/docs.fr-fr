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
# <a name="timers"></a><span data-ttu-id="c805d-103">Minuteries</span><span class="sxs-lookup"><span data-stu-id="c805d-103">Timers</span></span>

<span data-ttu-id="c805d-104">.NET propose deux minuteurs à utiliser dans un environnement multithread :</span><span class="sxs-lookup"><span data-stu-id="c805d-104">.NET provides two timers to use in a multithreaded environment:</span></span>

- <span data-ttu-id="c805d-105"><xref:System.Threading.Timer?displayProperty=nameWithType>, qui exécute une méthode de rappel unique sur un thread <xref:System.Threading.ThreadPool> à intervalles réguliers.</span><span class="sxs-lookup"><span data-stu-id="c805d-105"><xref:System.Threading.Timer?displayProperty=nameWithType>, which executes a single callback method on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>
- <span data-ttu-id="c805d-106"><xref:System.Timers.Timer?displayProperty=nameWithType> qui, par défaut, déclenche un événement sur un thread <xref:System.Threading.ThreadPool> à intervalles réguliers.</span><span class="sxs-lookup"><span data-stu-id="c805d-106"><xref:System.Timers.Timer?displayProperty=nameWithType>, which by default raises an event on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>

> [!NOTE]
> <span data-ttu-id="c805d-107">Certaines implémentations .NET peuvent inclure des minuteurs supplémentaires :</span><span class="sxs-lookup"><span data-stu-id="c805d-107">Some .NET implementations may include additional timers:</span></span>
>
> - <span data-ttu-id="c805d-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType> : composant Windows Forms qui déclenche un événement à intervalles réguliers.</span><span class="sxs-lookup"><span data-stu-id="c805d-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: a Windows Forms component that fires an event at regular intervals.</span></span> <span data-ttu-id="c805d-109">Le composant ne possède pas d’interface utilisateur et est conçu pour une utilisation dans un environnement à thread unique.</span><span class="sxs-lookup"><span data-stu-id="c805d-109">The component has no user interface and is designed for use in a single-threaded environment.</span></span>  
> - <span data-ttu-id="c805d-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType> : composant ASP.NET qui effectue des publications (postback) de pages web asynchrones ou synchrones à intervalles réguliers.</span><span class="sxs-lookup"><span data-stu-id="c805d-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: an ASP.NET component that performs asynchronous or synchronous web page postbacks at a regular interval.</span></span>
> - <span data-ttu-id="c805d-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType> : minuteur intégré à la file d’attente <xref:System.Windows.Threading.Dispatcher> qui est traitée selon un intervalle de temps et une priorité spécifiés.</span><span class="sxs-lookup"><span data-stu-id="c805d-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: a timer that is integrated into the <xref:System.Windows.Threading.Dispatcher> queue which is processed at a specified interval of time and at a specified priority.</span></span>

## <a name="the-systemthreadingtimer-class"></a><span data-ttu-id="c805d-112">Classe System.Threading.Timer</span><span class="sxs-lookup"><span data-stu-id="c805d-112">The System.Threading.Timer class</span></span>

<span data-ttu-id="c805d-113">La classe <xref:System.Threading.Timer?displayProperty=nameWithType> vous permet d’appeler en permanence un délégué à des intervalles de temps spécifiés.</span><span class="sxs-lookup"><span data-stu-id="c805d-113">The <xref:System.Threading.Timer?displayProperty=nameWithType> class enables you to continuously call a delegate at specified time intervals.</span></span> <span data-ttu-id="c805d-114">Vous pouvez également utiliser cette classe pour planifier un appel unique à un délégué dans un intervalle de temps spécifié.</span><span class="sxs-lookup"><span data-stu-id="c805d-114">You can also use this class to schedule a single call to a delegate in a specified time interval.</span></span> <span data-ttu-id="c805d-115">Le délégué est exécuté sur un thread <xref:System.Threading.ThreadPool>.</span><span class="sxs-lookup"><span data-stu-id="c805d-115">The delegate is executed on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="c805d-116">Quand vous créez un objet <xref:System.Threading.Timer?displayProperty=nameWithType>, vous spécifiez un délégué <xref:System.Threading.TimerCallback> qui définit la méthode de rappel, un objet d’état facultatif qui est passé au rappel, la durée d’attente avant la première invocation du rappel et l’intervalle de temps entre les invocations de rappel.</span><span class="sxs-lookup"><span data-stu-id="c805d-116">When you create a <xref:System.Threading.Timer?displayProperty=nameWithType> object, you specify a <xref:System.Threading.TimerCallback> delegate that defines the callback method, an optional state object that is passed to the callback, the amount of time to delay before the first invocation of the callback, and the time interval between callback invocations.</span></span> <span data-ttu-id="c805d-117">Pour annuler un minuteur en attente, appelez la méthode <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c805d-117">To cancel a pending timer, call the <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="c805d-118">L’exemple suivant crée un minuteur qui appelle le délégué fourni au bout d’une seconde (1000 millisecondes) la première fois et ensuite toutes les deux secondes.</span><span class="sxs-lookup"><span data-stu-id="c805d-118">The following example creates a timer that calls the provided delegate for the first time after one second (1000 milliseconds) and then calls it every two seconds.</span></span> <span data-ttu-id="c805d-119">L’objet d’état de l’exemple sert à compter le nombre de fois que le délégué est appelé.</span><span class="sxs-lookup"><span data-stu-id="c805d-119">The state object in the example is used to count how many times the delegate is called.</span></span> <span data-ttu-id="c805d-120">Le minuteur s’arrête dès que le délégué a été appelé au moins 10 fois.</span><span class="sxs-lookup"><span data-stu-id="c805d-120">The timer is stopped when the delegate has been called at least 10 times.</span></span>

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

<span data-ttu-id="c805d-121">Pour plus d’informations et d’exemples, consultez <xref:System.Threading.Timer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c805d-121">For more information and examples, see <xref:System.Threading.Timer?displayProperty=nameWithType>.</span></span>

## <a name="the-systemtimerstimer-class"></a><span data-ttu-id="c805d-122">Classe System.Timers.Timer</span><span class="sxs-lookup"><span data-stu-id="c805d-122">The System.Timers.Timer class</span></span>

<span data-ttu-id="c805d-123">L’autre minuteur qui peut être utilisé dans un environnement multithread est <xref:System.Timers.Timer?displayProperty=nameWithType> qui, par défaut, déclenche un événement sur un thread <xref:System.Threading.ThreadPool>.</span><span class="sxs-lookup"><span data-stu-id="c805d-123">Another timer that can be used in a multithreaded environment is <xref:System.Timers.Timer?displayProperty=nameWithType> that by default raises an event on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="c805d-124">Au moment de créer un objet <xref:System.Timers.Timer?displayProperty=nameWithType>, vous pouvez spécifier l’intervalle de temps au cours duquel un événement <xref:System.Timers.Timer.Elapsed> est déclenché.</span><span class="sxs-lookup"><span data-stu-id="c805d-124">When you create a <xref:System.Timers.Timer?displayProperty=nameWithType> object, you may specify the time interval in which to raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="c805d-125">Utilisez la propriété <xref:System.Timers.Timer.Enabled%2A> pour indiquer si un minuteur doit déclencher un événement <xref:System.Timers.Timer.Elapsed>.</span><span class="sxs-lookup"><span data-stu-id="c805d-125">Use the <xref:System.Timers.Timer.Enabled%2A> property to indicate if a timer should raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="c805d-126">Si vous avez besoin qu’un événement <xref:System.Timers.Timer.Elapsed> soit déclenché une seule fois à l’issue de l’intervalle spécifié, définissez le <xref:System.Timers.Timer.AutoReset%2A> sur `false`.</span><span class="sxs-lookup"><span data-stu-id="c805d-126">If you need an <xref:System.Timers.Timer.Elapsed> event to be raised only once after the specified interval has elapsed, set the <xref:System.Timers.Timer.AutoReset%2A> to `false`.</span></span> <span data-ttu-id="c805d-127">La valeur par défaut de la propriété <xref:System.Timers.Timer.AutoReset%2A> est `true`, ce qui signifie qu’un événement <xref:System.Timers.Timer.Elapsed> est déclenché régulièrement selon l’intervalle défini par la propriété <xref:System.Timers.Timer.Interval%2A>.</span><span class="sxs-lookup"><span data-stu-id="c805d-127">The default value of the <xref:System.Timers.Timer.AutoReset%2A> property is `true`, which means that an <xref:System.Timers.Timer.Elapsed> event is raised regularly at the interval defined by the <xref:System.Timers.Timer.Interval%2A> property.</span></span>

<span data-ttu-id="c805d-128">Pour plus d’informations et d’exemples, consultez <xref:System.Timers.Timer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c805d-128">For more information and examples, see <xref:System.Timers.Timer?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c805d-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c805d-129">See also</span></span>

- <xref:System.Threading.Timer?displayProperty=nameWithType>
- <xref:System.Timers.Timer?displayProperty=nameWithType>
- [<span data-ttu-id="c805d-130">Fonctionnalités et objets de threading</span><span class="sxs-lookup"><span data-stu-id="c805d-130">Threading Objects and Features</span></span>](threading-objects-and-features.md)
