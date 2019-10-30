---
title: 'Comment : activer un WebRequest pour utiliser un proxy pour communiquer avec Internet'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: 8b38973e4cb2c83ce32b8a08e54d828a8eeef879
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039538"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a>Comment : activer un WebRequest pour utiliser un proxy pour communiquer avec Internet

Cet exemple crée une instance proxy globale qui permet à tout <xref:System.Net.WebRequest> d’utiliser un proxy pour communiquer avec Internet. L’exemple suppose que le serveur proxy est nommé `webproxy` et qu’il communique sur le port 80, le port HTTP standard.

## <a name="example"></a>Exemple

```csharp
var proxyObject = new WebProxy("http://webproxy:80/");
GlobalProxySelection.Select = proxyObject;
```

```vb
Dim proxyObject As New WebProxy("http://webproxy:80/")
GlobalProxySelection.Select = proxyObject
```

## <a name="compiling-the-code"></a>Compilation du code

Cet exemple nécessite :

- C# [Directive`using`](../../csharp/language-reference/keywords/using-directive.md) pour l’espace de noms **System.net** .
- Visual Basic [`Imports` instruction](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pour l’espace de noms **System.net** .

## <a name="see-also"></a>Voir aussi

- [Utilisation de protocoles d’application](using-application-protocols.md)
- [Accès à Internet via un proxy](accessing-the-internet-through-a-proxy.md)
