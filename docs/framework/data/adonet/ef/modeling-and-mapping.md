---
title: Modélisation et mappage
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: 133539ab1b6d6f2f0ab3f8deed5b22240c2bb07e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854394"
---
# <a name="modeling-and-mapping"></a>Modélisation et mappage
Dans l’Entity Framework, vous pouvez définir le modèle conceptuel, le modèle de stockage et le mappage entre les deux de la manière la mieux adaptée à votre application. Les outils de Entity Data Model dans Visual Studio vous permettent de créer un. [fichier edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)) à partir d’une base de données ou d’un modèle graphique, puis mettez à jour ce fichier lorsque la base de données ou le modèle change.  
  
 Depuis Entity Framework 4.1, vous pouvez également créer un modèle par programme à l'aide du développement Code First. Il existe deux scénarios différents pour le développement Code First. Dans les deux cas, le développeur définit un modèle lors du codage des définitions de classe .NET Framework, puis spécifie éventuellement un mappage supplémentaire ou une configuration supplémentaire à l'aide des annotations de données ou de l'API Fluent.  
  
 Pour plus d’informations, consultez [création et mappage d’un modèle conceptuel](https://go.microsoft.com/fwlink/?LinkId=235016).  
  
 Vous pouvez également utiliser le générateur EDM, qui est inclus avec le .NET Framework. EdmGen.exe génère les fichiers .csdl, .ssdl et .msl d'une source de données existante. Vous pouvez également créer manuellement le modèle et mapper le contenu. Pour plus d’informations, consultez [EDM Generator (EdmGen. exe)](edm-generator-edmgen-exe.md).
