---
ms.openlocfilehash: b893966ceb65246ed6a7d214011b17ca14c50d5a
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85802847"
---

> [!WARNING]
> Lorsque <xref:System.Text.RegularExpressions> vous utilisez pour traiter une entrée non fiable, transmettez un délai d’attente. Un utilisateur malveillant peut fournir une entrée pour `RegularExpressions` provoquer une [attaque par déni de service](https://www.us-cert.gov/ncas/tips/ST04-015). ASP.NET Core les API d’infrastructure qui utilisent `RegularExpressions` passent un délai d’expiration.
