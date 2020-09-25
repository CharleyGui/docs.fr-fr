---
title: Modélisation et mappage
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: 5592ce5301216c8c3e74231480997d9e44d71a7d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197753"
---
# <a name="modeling-and-mapping"></a>Modélisation et mappage

Dans l’Entity Framework, vous pouvez définir le modèle conceptuel, le modèle de stockage et le mappage entre les deux de la manière la mieux adaptée à votre application. Les outils de Entity Data Model dans Visual Studio vous permettent de créer un. [fichier edmx](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)) à partir d’une base de données ou d’un modèle graphique, puis mettez à jour ce fichier lorsque la base de données ou le modèle change.  
  
 Depuis Entity Framework 4.1, vous pouvez également créer un modèle par programme à l'aide du développement Code First. Il existe deux scénarios différents pour le développement Code First. Dans les deux cas, le développeur définit un modèle lors du codage des définitions de classe .NET Framework, puis spécifie éventuellement un mappage supplémentaire ou une configuration supplémentaire à l'aide des annotations de données ou de l'API Fluent.  
  
 Pour plus d’informations, consultez [création d’un modèle](/ef/ef6/modeling/).  
  
 Vous pouvez également utiliser le générateur EDM, qui est inclus avec le .NET Framework. EdmGen.exe génère les fichiers .csdl, .ssdl et .msl d'une source de données existante. Vous pouvez également créer manuellement le modèle et mapper le contenu. Pour plus d’informations, consultez [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md).
