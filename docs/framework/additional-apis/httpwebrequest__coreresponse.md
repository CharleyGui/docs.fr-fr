---
title: HttpWebRequest. _CoreResponse Field
description: En savoir plus sur le champ HttpWebRequest. _CoreResponse dans .NET. Ce champ est un objet CoreResponseData ou exception contenant le résultat de l’analyse de la réponse HTTP.
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.HttpWebRequest._CoreResponse
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: 5093ec7ed2c3b94931dcd622ae9ccdb42feffa18
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989746"
---
# <a name="httpwebrequest_coreresponse-field"></a>HttpWebRequest. \_ Champ CoreResponse

`HttpWebRequest._CoreResponse`est un objet ( [CoreResponseData](coreresponsedata.md) ou <xref:System.Exception> ) qui contient le résultat de l’analyse de la réponse http.

## <a name="syntax"></a>Syntax
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> Cette API n’est pas destinée à être utilisée directement dans votre code. Au lieu de cela, vous devez utiliser un <xref:System.Diagnostics.DiagnosticSource> pour raccorder du code de mise en réseau. Consultez le [Guide de l’utilisateur DiagnosticSource](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).
>
> Microsoft ne prend pas en charge l’utilisation de cette classe dans une application de production en l’absence de toute circonstance.

## <a name="requirements"></a>Spécifications

**Espace de noms :** <xref:System.Net>

**Assembly :** Système (en System.dll)

**Versions de .NET Framework :** Disponible depuis 2,0.
