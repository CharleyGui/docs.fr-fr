---
title: Interopérabilité - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: b568bdc149123b490f3b058afc668aabcf558d55
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65585463"
---
# <a name="interoperability-c-programming-guide"></a>Interopérabilité (Guide de programmation C#)
L’interopérabilité vous permet de préserver et de tirer parti d’investissements existants en code non managé. Le code qui s’exécute sous le contrôle du common language runtime (CLR) est appelé *code managé*, et le code qui s’exécute en dehors du CLR est appelé *code non managé*. COM, COM+, les composants C++, les composants ActiveX et l’API Microsoft Windows sont des exemples de code non managé.  
  
 Le .NET Framework permet l’interopérabilité avec du code non managé par des services d’appel de code non managé, l’espace de noms <xref:System.Runtime.InteropServices>, l’interopérabilité C++ et l’interopérabilité COM (COM Interop).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble de l’interopérabilité](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 Décrit les méthodes qui permettent l’interopérabilité entre le code managé et le code non managé en C#.  
  
 [Guide pratique pour accéder aux objets Office Interop à l’aide des fonctionnalités Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 Décrit les fonctionnalités introduites dans Visual C# pour faciliter la programmation Office.  
  
 [Guide pratique pour utiliser des propriétés indexées dans la programmation COM Interop](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 Explique comment utiliser des propriétés indexées pour accéder aux propriétés COM qui ont des paramètres.  
  
 [Guide pratique pour utiliser l’appel de code non managé pour lire un fichier audio](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 Explique comment utiliser des services d’appel de code non managé pour lire un fichier son .wav sur le système d’exploitation Windows.  
  
 [Procédure pas à pas : programmation Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 Montre comment créer un classeur Excel et un document Word qui contient un lien vers le classeur.  
  
 [Exemple de classe COM](../../../csharp/programming-guide/interop/example-com-class.md)  
 Montre comment exposer une classe C# en tant qu’objet COM.  
  
## <a name="c-language-specification"></a>Spécification du langage C#  

Pour plus d’informations, consultez [Concepts de base](~/_csharplang/spec/unsafe-code.md) dans la [Spécification du langage C#](../../language-reference/language-specification/index.md). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [Guide de programmation C#](../../../csharp/programming-guide/index.md)
- [Interopération avec du code non managé](../../../../docs/framework/interop/index.md)
- [Procédure pas à pas : programmation Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
