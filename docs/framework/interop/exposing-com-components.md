---
title: Exposition de composants COM au .NET Framework
description: Découvrez le processus d’exposition des composants COM à .NET. Les composants COM sont utiles dans du code managé en tant qu’applications métier de couche intermédiaire ou fonctionnalités isolées.
ms.date: 03/30/2017
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
ms.openlocfilehash: 4e18e3f49dacbb3a358aa7e9785a5dda93206164
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267063"
---
# <a name="exposing-com-components-to-the-net-framework"></a>Exposition de composants COM au .NET Framework

Cette section résume le processus nécessaire pour exposer un composant COM existant à du code managé. Pour plus d’informations sur l’écriture de serveurs COM qui s’intègrent étroitement au .NET Framework, consultez [Considérations de design pour l’interopérabilité](/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).
  
 Les composants COM existants sont des ressources importantes dans le code managé, en tant qu’applications métier de couche intermédiaire ou en tant que fonctionnalités isolées. Un composant idéal a un assembly PIA et se conforme étroitement aux normes de programmation imposées par COM.  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a>Pour exposer des composants COM au .NET Framework  
  
1. [Importation d’une bibliothèque de types sous la forme d’un assembly](importing-a-type-library-as-an-assembly.md).  
  
     Le common language runtime nécessite des métadonnées pour tous les types, y compris les types COM. Il existe plusieurs manières d’obtenir un assembly contenant des types COM importés en tant que métadonnées.  
  
2. [Utilisation de types COM dans du code managé](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).  
  
     Vous pouvez inspecter des types COM, activer des instances et appeler des méthodes sur l’objet COM de la même façon que vous le feriez pour n’importe quel type managé.  
  
3. [Compilation d’un projet d’interopérabilité](compiling-an-interop-project.md).  
  
     Le SDK Windows fournit des compilateurs pour plusieurs langages conformes à la spécification CLS (Common Language Specification), notamment Visual Basic, C# et C++.  
  
4. [Déploiement d’une application d’interopérabilité](deploying-an-interop-application.md).  
  
     La meilleure façon de déployer des applications d’interopérabilité est de le faire en tant qu’assemblys signés [avec nom fort](../../standard/assembly/strong-named.md) dans le Global Assembly Cache.  
  
## <a name="see-also"></a>Voir aussi

- [Interopération avec du code non managé](index.md)
- [Considérations relatives à la conception de l’interopérabilité](/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))
- [Exemple COM Interop : client .NET et serveur COM](com-interop-sample-net-client-and-com-server.md)
- [Indépendance du langage et composants indépendants du langage](../../standard/language-independence-and-language-independent-components.md)
- [Gacutil.exe (Outil Global Assembly Cache)](../tools/gacutil-exe-gac-tool.md)
