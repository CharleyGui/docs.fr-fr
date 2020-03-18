---
title: Interopérabilité - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: 3a70d2ae077552bab536e96367cab0fda1661310
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75712050"
---
# <a name="interoperability-c-programming-guide"></a>Interopérabilité (Guide de programmation C#)
L’interopérabilité vous permet de préserver et de tirer parti d’investissements existants en code non managé. Le code qui s’exécute sous le contrôle du common language runtime (CLR) est appelé *code managé*, et le code qui s’exécute en dehors du CLR est appelé *code non managé*. COM, COM+, les composants C++, les composants ActiveX et l’API Microsoft Windows sont des exemples de code non managé.  
  
 Le .NET Framework permet l’interopérabilité avec du code non managé par des services d’appel de code non managé, l’espace de noms <xref:System.Runtime.InteropServices>, l’interopérabilité C++ et l’interopérabilité COM (COM Interop).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble de l’interopérabilité](./interoperability-overview.md)  
 Décrit les méthodes qui permettent l’interopérabilité entre le code managé et le code non managé en C#.  
  
 [Comment accéder aux objets Office Interop à l’aide des fonctionnalités C#](./how-to-access-office-onterop-objects.md)  
 Décrit les fonctionnalités introduites dans Visual C# pour faciliter la programmation Office.  
  
 [Comment utiliser des propriétés indexées dans la programmation COM Interop](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 Explique comment utiliser des propriétés indexées pour accéder aux propriétés COM qui ont des paramètres.  
  
 [Comment utiliser l’appel de code non managé pour lire un fichier WAV](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 Explique comment utiliser des services d’appel de code non managé pour lire un fichier son .wav sur le système d’exploitation Windows.  
  
 [Procédure pas à pas : programmation Office](./walkthrough-office-programming.md)  
 Montre comment créer un classeur Excel et un document Word qui contient un lien vers le classeur.  
  
 [Exemple de classe COM](./example-com-class.md)  
 Montre comment exposer une classe C# en tant qu’objet COM.  
  
## <a name="c-language-specification"></a>Spécification du langage C#  

Pour plus d’informations, consultez [Concepts de base](~/_csharplang/spec/unsafe-code.md) dans la [Spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [Guide de programmation C#](../index.md)
- [Interopération avec code non traité](../../../framework/interop/index.md)
- [Procédure pas à pas : programmation Office](./walkthrough-office-programming.md)
