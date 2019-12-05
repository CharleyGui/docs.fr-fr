---
title: Enregistrements de suivi personnalisé
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: 986f0350c24414d0ff960474445adf6ac3f39734
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802620"
---
# <a name="custom-tracking-records"></a><span data-ttu-id="d0ee4-102">Enregistrements de suivi personnalisé</span><span class="sxs-lookup"><span data-stu-id="d0ee4-102">Custom Tracking Records</span></span>

<span data-ttu-id="d0ee4-103">Cette rubrique montre comment créer des enregistrements de suivi personnalisés et les remplir avec des données à émettre avec les enregistrements.</span><span class="sxs-lookup"><span data-stu-id="d0ee4-103">This topic demonstrates how to create custom tracking records and populate them with data to be emitted along with the records.</span></span>

## <a name="emitting-custom-tracking-records"></a><span data-ttu-id="d0ee4-104">Émission d'enregistrements de suivi personnalisé</span><span class="sxs-lookup"><span data-stu-id="d0ee4-104">Emitting Custom Tracking Records</span></span>

<span data-ttu-id="d0ee4-105">Les enregistrements de suivi personnalisés peuvent être issus d'une activité de code comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="d0ee4-105">Custom tracking records can be emitted from a code activity as shown in the following example.</span></span>

```csharp
protected override void Execute(CodeActivityContext context)
{
…
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");
            customRecord.Data.Add("SendTime", sendTime);
            context.Track(customRecord);
}
```

<span data-ttu-id="d0ee4-106">Un <xref:System.Activities.Tracking.CustomTrackingRecord> est émis dans une activité de code en appelant la méthode <xref:System.Activities.NativeActivityContext.Track%2A> sur `ActivityContext`.</span><span class="sxs-lookup"><span data-stu-id="d0ee4-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted in a code activity by invoking the <xref:System.Activities.NativeActivityContext.Track%2A> method on the `ActivityContext`.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0ee4-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0ee4-107">See also</span></span>

- <span data-ttu-id="d0ee4-108">[Analyse Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="d0ee4-108">[Windows Server App Fabric Monitoring](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="d0ee4-109">[Surveillance des applications avec application Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="d0ee4-109">[Monitoring Applications with App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
