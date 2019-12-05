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
# <a name="custom-tracking-records"></a>Enregistrements de suivi personnalisé

Cette rubrique montre comment créer des enregistrements de suivi personnalisés et les remplir avec des données à émettre avec les enregistrements.

## <a name="emitting-custom-tracking-records"></a>Émission d'enregistrements de suivi personnalisé

Les enregistrements de suivi personnalisés peuvent être issus d'une activité de code comme indiqué dans l'exemple suivant.

```csharp
protected override void Execute(CodeActivityContext context)
{
…
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");
            customRecord.Data.Add("SendTime", sendTime);
            context.Track(customRecord);
}
```

Un <xref:System.Activities.Tracking.CustomTrackingRecord> est émis dans une activité de code en appelant la méthode <xref:System.Activities.NativeActivityContext.Track%2A> sur `ActivityContext`.

## <a name="see-also"></a>Voir aussi

- [Analyse Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))
- [Surveillance des applications avec application Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))
