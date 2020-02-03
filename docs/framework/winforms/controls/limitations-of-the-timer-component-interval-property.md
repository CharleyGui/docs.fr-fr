---
title: Limitations de la propriété intervalle du composant Timer
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: 15626a53f0541ff79e2098377d9dfdb4626ac155
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745234"
---
# <a name="limitations-of-the-windows-forms-timer-components-interval-property"></a><span data-ttu-id="81fe7-102">Restrictions relatives à la propriété Interval du composant Timer Windows Forms</span><span class="sxs-lookup"><span data-stu-id="81fe7-102">Limitations of the Windows Forms Timer Component's Interval Property</span></span>
<span data-ttu-id="81fe7-103">Le composant Windows Forms <xref:System.Windows.Forms.Timer> a une propriété <xref:System.Windows.Forms.Timer.Interval%2A> qui spécifie le nombre de millisecondes qui passent entre un événement de minuterie et le suivant.</span><span class="sxs-lookup"><span data-stu-id="81fe7-103">The Windows Forms <xref:System.Windows.Forms.Timer> component has an <xref:System.Windows.Forms.Timer.Interval%2A> property that specifies the number of milliseconds that pass between one timer event and the next.</span></span> <span data-ttu-id="81fe7-104">À moins que le composant ne soit désactivé, un minuteur continue de recevoir l’événement <xref:System.Windows.Forms.Timer.Tick> à des intervalles de temps à peu près égaux.</span><span class="sxs-lookup"><span data-stu-id="81fe7-104">Unless the component is disabled, a timer continues to receive the <xref:System.Windows.Forms.Timer.Tick> event at roughly equal intervals of time.</span></span>  
  
 <span data-ttu-id="81fe7-105">Ce composant est conçu pour un environnement Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="81fe7-105">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="81fe7-106">Si vous avez besoin d’un minuteur adapté à un environnement de serveur, consultez l’article [Introduction aux minuteurs serveur](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="81fe7-106">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
## <a name="the-interval-property"></a><span data-ttu-id="81fe7-107">La propriété Interval</span><span class="sxs-lookup"><span data-stu-id="81fe7-107">The Interval Property</span></span>  
 <span data-ttu-id="81fe7-108">La propriété <xref:System.Windows.Forms.Timer.Interval%2A> présente quelques limitations à prendre en compte lors de la programmation d’un composant <xref:System.Windows.Forms.Timer> :</span><span class="sxs-lookup"><span data-stu-id="81fe7-108">The <xref:System.Windows.Forms.Timer.Interval%2A> property has a few limitations to consider when you are programming a <xref:System.Windows.Forms.Timer> component:</span></span>  
  
- <span data-ttu-id="81fe7-109">Si votre application ou une autre application fait des demandes importantes sur le système (par exemple, des boucles longues, des calculs intensifs ou un accès à un lecteur, un réseau ou un port), votre application peut ne pas recevoir d’événements de minuteur aussi souvent que la propriété <xref:System.Windows.Forms.Timer.Interval%2A> spécifie.</span><span class="sxs-lookup"><span data-stu-id="81fe7-109">If your application or another application is making heavy demands on the system — such as long loops, intensive calculations, or drive, network, or port access — your application may not get timer events as often as the <xref:System.Windows.Forms.Timer.Interval%2A> property specifies.</span></span>  
  
- <span data-ttu-id="81fe7-110">Il n’est pas garanti que l’intervalle s’écoule exactement dans le temps.</span><span class="sxs-lookup"><span data-stu-id="81fe7-110">The interval is not guaranteed to elapse exactly on time.</span></span> <span data-ttu-id="81fe7-111">Pour garantir la précision, la minuterie doit vérifier l’horloge système si nécessaire, plutôt que d’essayer d’effectuer le suivi du temps accumulé en interne.</span><span class="sxs-lookup"><span data-stu-id="81fe7-111">To ensure accuracy, the timer should check the system clock as needed, rather than try to keep track of accumulated time internally.</span></span>  
  
- <span data-ttu-id="81fe7-112">La précision de la propriété de <xref:System.Windows.Forms.Timer.Interval%2A> est exprimée en millisecondes.</span><span class="sxs-lookup"><span data-stu-id="81fe7-112">The precision of the <xref:System.Windows.Forms.Timer.Interval%2A> property is in milliseconds.</span></span> <span data-ttu-id="81fe7-113">Certains ordinateurs fournissent un compteur haute résolution dont la résolution est supérieure à millisecondes.</span><span class="sxs-lookup"><span data-stu-id="81fe7-113">Some computers provide a high-resolution counter that has a resolution higher than milliseconds.</span></span> <span data-ttu-id="81fe7-114">La disponibilité d’un tel compteur dépend du matériel du processeur de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="81fe7-114">The availability of such a counter depends on the processor hardware of your computer.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="81fe7-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81fe7-115">See also</span></span>

- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="81fe7-116">Timer, composant</span><span class="sxs-lookup"><span data-stu-id="81fe7-116">Timer Component</span></span>](timer-component-windows-forms.md)
- [<span data-ttu-id="81fe7-117">Vue d’ensemble du composant Timer</span><span class="sxs-lookup"><span data-stu-id="81fe7-117">Timer Component Overview</span></span>](timer-component-overview-windows-forms.md)
