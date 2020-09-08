---
title: Guide pratique pour générer des exemples LINQ to XML
description: Le code C# et Visual Basic de cette documentation utilise des classes et des types de différents espaces de noms. Pour compiler et exécuter le code, vous devez fournir des directives et des instructions appropriées pour accéder aux espaces de noms.
ms.date: 07/20/2015
ms.assetid: e5d18fa1-2704-48fe-a44b-1564f97c9e9c
ms.openlocfilehash: 94b2368e2c861f84d7db08fbbba57ef0f0da4d40
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552461"
---
# <a name="how-to-build-linq-to-xml-examples"></a>Guide pratique pour générer des exemples LINQ to XML

Les extraits et les exemples de cette documentation utilisent des classes et des types de différents espaces de noms. Lors de la compilation de code C#, vous devez fournir `using` des directives appropriées et, lors de la compilation de Visual Basic Code, vous devez fournir les `Imports` instructions appropriées.

## <a name="example"></a>Exemple

Le code suivant contient les directives `using` requises pour la génération et l'exécution des exemples C#. Toutes les directives `using` ne sont pas requises pour tous les exemples.

```csharp
using System;
using System.Diagnostics;
using System.Collections;
using System.Collections.Generic;
using System.Collections.Specialized;
using System.Text;
using System.Linq;
using System.Xml;
using System.Xml.Linq;
using System.Xml.Schema;
using System.Xml.XPath;
using System.Xml.Xsl;
using System.IO;
using System.Threading;
using System.Reflection;
using System.IO.Packaging;
```

Le code suivant contient les instructions `Imports` requises pour la génération et l'exécution des exemples Visual Basic. Toutes les instructions `Imports` ne sont pas requises pour tous les exemples.

```vb
Imports System.Diagnostics
Imports System.Collections
Imports System.Collections.Generic
Imports System.Collections.Specialized
Imports System.Text
Imports System.Linq
Imports System.Xml
Imports System.Xml.Linq
Imports System.Xml.Schema
Imports System.Xml.XPath
Imports System.Xml.Xsl
Imports System.IO
Imports System.Threading
Imports System.Reflection
Imports System.IO.Packaging
```

## <a name="see-also"></a>Voir aussi

- [Présentation de LINQ to XML](linq-xml-overview.md)
