---
title: Classe de journalisation (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Logging
- System.Net.Logging.Associate
- System.Net.Logging.Enter
- System.Net.Logging.Exception
- System.Net.Logging.Exit
- System.Net.Logging.get_Http
- System.Net.Logging.get_On
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: ad85fdd41252ed147eb5fe1a9db029db046d720c
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990389"
---
# <a name="logging-class"></a>Logging, classe

Fournit la fonctionnalité de journalisation de suivi.

```csharp
internal class Logging
```

> [!WARNING]
> Cette classe est interne et n’est pas destinée à être utilisée directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de cette classe dans une application de production en l’absence de toute circonstance.

## <a name="associate-method"></a>Méthode Associate

Journalise les informations auxquelles deux objets sont associés.

```csharp
internal static void Associate(TraceSource traceSource, object objA, object objB)
```

### <a name="parameters"></a>Paramètres

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Source de suivi dans laquelle enregistrer l’événement.

- `objA` <xref:System.Object>

  Objet à associer à `objB` .

- `objB` <xref:System.Object>

  Objet à associer à `objA` .

## <a name="entertracesource-object-string-string-method"></a>Enter (TraceSource, Object, String, String), méthode

Journalise l’entrée dans une méthode.

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, string param)
```

### <a name="parameters"></a>Paramètres

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Source de suivi dans laquelle enregistrer l’événement.

- `obj` <xref:System.Object>

  Objet sur lequel la méthode a été appelée.

- `method` <xref:System.String>

  Méthode entrée.

- `param` <xref:System.String>

  Paramètres passés à la méthode.

## <a name="entertracesource-object-string-object-method"></a>Enter (TraceSource, Object, String, Object), méthode

Journalise l’entrée dans une méthode.

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, object paramObject)
```

### <a name="parameters"></a>Paramètres

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Source de suivi dans laquelle enregistrer l’événement.

- `obj` <xref:System.Object>

  Objet sur lequel la méthode a été appelée.

- `method` <xref:System.String>

  Méthode entrée.

- `paramObject` <xref:System.Object>

  Paramètres passés à la méthode.

## <a name="entertracesource-string-string-string-method"></a>Enter (TraceSource, String, String, String), méthode

Journalise l’entrée dans une méthode.

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, string param)
```

### <a name="parameters"></a>Paramètres

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Source de suivi dans laquelle enregistrer l’événement.

- `obj` <xref:System.String>

  Objet sur lequel la méthode a été appelée.

- `method` <xref:System.String>

  Méthode entrée.

- `param` <xref:System.String>

  Paramètres passés à la méthode.

## <a name="entertracesource-string-string-object-method"></a>Enter (TraceSource, String, String, Object), méthode

Journalise l’entrée dans une méthode.

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, object paramObject)
```

### <a name="parameters"></a>Paramètres

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Source de suivi dans laquelle enregistrer l’événement.

- `obj` <xref:System.String>

  Objet sur lequel la méthode a été appelée.

- `method` <xref:System.String>

  Méthode entrée.

- `paramObject` <xref:System.Object>

  Paramètres passés à la méthode.

## <a name="entertracesource-string-string-method"></a>Méthode Enter (TraceSource, String, String)

Journalise l’entrée dans une méthode.

```csharp
internal static void Enter(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a>Paramètres

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Source de suivi dans laquelle enregistrer l’événement.

- `method` <xref:System.String>

  Méthode entrée.

- `parameters` <xref:System.String>

  Paramètres passés à la méthode.

## <a name="entertracesource-string-method"></a>Enter (TraceSource, String), méthode

Journalise l’entrée dans une méthode.

```csharp
internal static void Enter(TraceSource traceSource, string msg)
```

### <a name="parameters"></a>Paramètres

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Source de suivi dans laquelle enregistrer l’événement.

- `msg` <xref:System.String>

  Message d’entrée à enregistrer dans la source de la trace.

## <a name="exception-method"></a>Exception (méthode)

Journalise une exception et restaure la mise en retrait.

```csharp
internal static void Exception(TraceSource traceSource, object obj, string method, Exception e)
```

### <a name="parameters"></a>Paramètres

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Source de suivi dans laquelle enregistrer l’événement.

- `obj` <xref:System.Object>

  Objet sur lequel la méthode qui a levé une exception a été appelée.

- `method` <xref:System.String>

  Méthode qui a levé l’exception.

- `e` <xref:System.Exception>

  Exception qui a été levée.

## <a name="exittracesource-object-string-object-method"></a>Exit (TraceSource, Object, String, Object), méthode

Les journaux quittent une fonction.

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, object retObject)
```

### <a name="parameters"></a>Paramètres

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Source de suivi dans laquelle enregistrer l’événement.

- `obj` <xref:System.Object>

  Objet sur lequel la méthode a été appelée.

- `method` <xref:System.String>

  Méthode en cours de sortie.

- `retObject` <xref:System.Object>

  Valeur retournée par la méthode.

## <a name="exittracesource-string-string-object-method"></a>Exit (TraceSource, String, String, Object), méthode

Les journaux quittent une fonction.

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, object retObject)
```

### <a name="parameters"></a>Paramètres

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Source de suivi dans laquelle enregistrer l’événement.

- `obj` <xref:System.String>

  Objet sur lequel la méthode a été appelée.

- `method` <xref:System.String>

  Méthode en cours de sortie.

- `retObject` <xref:System.Object>

  Valeur retournée par la méthode.

## <a name="exittracesource-object-string-string-method"></a>Exit (TraceSource, Object, String, String), méthode

Les journaux quittent une fonction.

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, string retValue)
```

### <a name="parameters"></a>Paramètres

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Source de suivi dans laquelle enregistrer l’événement.

- `obj` <xref:System.Object>

  Objet sur lequel la méthode a été appelée.

- `method` <xref:System.String>

  Méthode en cours de sortie.

- `retValue` <xref:System.String>

  Valeur retournée par la méthode.

## <a name="exittracesource-string-string-string-method"></a>Exit (TraceSource, String, String, String), méthode

Les journaux quittent une fonction.

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, string retValue)
```

### <a name="parameters"></a>Paramètres

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Source de suivi dans laquelle enregistrer l’événement.

- `obj` <xref:System.String>

  Objet sur lequel la méthode a été appelée.

- `method` <xref:System.String>

  Méthode en cours de sortie.

- `retValue` <xref:System.String>

  Valeur retournée par la méthode.

## <a name="exittracesource-string-string-method"></a>Exit (TraceSource, String, String), méthode

Les journaux quittent une fonction.

```csharp
internal static void Exit(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a>Paramètres

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Source de suivi dans laquelle enregistrer l’événement.

- `method` <xref:System.String>

  Méthode en cours de sortie.

- `parameters` <xref:System.String>

  Paramètres passés à la méthode en cours de sortie.

## <a name="exittracesource-string-method"></a>Exit (TraceSource, String), méthode

Les journaux quittent une fonction.

```csharp
internal static void Exit(TraceSource traceSource, string msg)
```

### <a name="parameters"></a>Paramètres

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Source de suivi dans laquelle enregistrer l’événement.

- `msg` <xref:System.String>

  Message de sortie à enregistrer dans la source de la trace.

## <a name="http-property"></a>Propriété http

Obtient la source de suivi pour « System .net. http ».

```csharp
internal static TraceSource Http { get; }
```

### <a name="property-value"></a>Valeur de la propriété

<xref:System.Diagnostics.TraceSource>\
Source de suivi pour « System .net. http », ou `null` si la journalisation n’est pas activée.

## <a name="on-property"></a>Sur la propriété

Obtient une valeur qui indique si la journalisation est activée.

```csharp
internal static bool On { get; }
```

### <a name="property-value"></a>Valeur de la propriété

<xref:System.Boolean>\
`true` si la journalisation est activée ; sinon `false`.

## <a name="requirements"></a>Spécifications

**Espace de noms :** <xref:System.Net>

**Assembly :** Système (en System.dll)
