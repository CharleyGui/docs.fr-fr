---
title: Programmation à l'aide de domaines d'application et d'assemblys
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
ms.openlocfilehash: 3f66eacaf30f8001cdbf3a486e5ce1c878712e2f
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644274"
---
# <a name="programming-with-application-domains-and-assemblies"></a>Programmation à l'aide de domaines d'application et d'assemblys

Les ordinateurs hôtes tels que Microsoft Internet Explorer, ASP.NET et le shell Windows chargent le Common Language Runtime dans un processus, créent un [domaine d’application](application-domains.md) dans ce processus, puis chargent et exécutent le code utilisateur dans ce domaine d’application lors de l’exécution d’une application .NET Framework. Dans la plupart des cas, vous n’avez pas à vous soucier de la création des domaines d’application et du chargement des assemblys dans ces domaines car l’hôte runtime effectue ces tâches.  
  
Toutefois, si vous créez une application qui hébergera le Common Language Runtime, créez des outils ou un code que vous souhaitez décharger par programmation, ou créez des composants enfichables pouvant être déchargés et rechargés à la volée, vous allez créer vos propres domaines d’application. Même si vous ne créez aucun hôte de runtime, cette section fournit des informations importantes sur l’utilisation des domaines d’application et assemblys chargés dans ces domaines d’application.  
  
## <a name="in-this-section"></a>Dans cette section  

[Rubriques Guide pratique relatives aux domaines d'application et aux assemblys](application-domains-and-assemblies-how-to-topics.md)  
Fournit des liens vers toutes les rubriques Guide pratique de la documentation conceptuelle pour la programmation avec des domaines d’application et des assemblys.  
  
[Utilisation des domaines d’application](use.md)  
Fournit des exemples de création, de configuration et d’utilisation des domaines d’application.  
  
[Programmation à l’aide d’assemblys](../../standard/assembly/index.md)  
Décrit comment créer, signer et définir des attributs sur des assemblys.  
  
## <a name="related-sections"></a>Sections connexes  

[Émission d’assemblys et de méthodes dynamiques](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
Décrit comment créer des assemblys dynamiques.  
  
[Assemblys dans .NET](../../standard/assembly/index.md)  
Fournit une vue d'ensemble conceptuelle des assemblys.  
  
[Domaines d'application](application-domains.md)  
Fournit une vue d'ensemble conceptuelle des domaines d'application.  
  
[Vue d’ensemble de la réflexion](../reflection-and-codedom/reflection.md)  
Explique comment utiliser la classe **Reflection** pour obtenir des informations sur un assembly.
