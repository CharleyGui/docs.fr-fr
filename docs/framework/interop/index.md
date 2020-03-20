---
title: Interopération avec du code non managé
ms.date: 01/17/2018
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
ms.openlocfilehash: 12183f390a5178f038c6dd2122a72a33e31ae0ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457970"
---
# <a name="interoperating-with-unmanaged-code"></a>Interopération avec du code non managé

Le .NET Framework assure l’interaction avec les composants COM, les services COM+, les bibliothèques de types externes et de nombreux services de systèmes d’exploitation. Les types de données, les signatures de méthode et les mécanismes de gestion des erreurs varient selon les modèles objet managés et non managés. Pour simplifier l’interopérabilité entre les composants .NET Framework et le code non managé ainsi que pour faciliter la migration, le common language runtime dissimule à la fois aux clients et aux serveurs les différences entre ces modèles objet.

Le code qui s’exécute sous le contrôle du runtime est appelé code managé. Inversement, le code qui s’exécute en dehors du runtime est appelé code non managé. Les composants COM, les interfaces ActiveX et les fonctions API Windows sont des exemples de code non managé.

## <a name="in-this-section"></a>Contenu de cette section

[Exposition de composants COM au .NET Framework](exposing-com-components.md)  
Explique comment utiliser des composants COM à partir d’applications .NET Framework.

[Exposition de composants .NET Framework à COM](exposing-dotnet-components-to-com.md)  
Explique comment utiliser des composants .NET Framework à partir d’applications COM.

[Consommation de fonctions DLL non managées](consuming-unmanaged-dll-functions.md)  
Décrit comment appeler des fonctions DLL non managées à l’aide de l’appel de code non managé.

[Marshaling d’interopérabilité](interop-marshaling.md)  
Décrit le marshaling de COM Interop et de l’appel de code non managé.

[Guide pratique pour mapper des HRESULT et des exceptions](how-to-map-hresults-and-exceptions.md)  
Décrit le mappage entre les exceptions et les valeurs HRESULT.

[Équivalence de type et types interop incorporés](type-equivalence-and-embedded-interop-types.md)  
Décrit comment les informations de type pour les types COM sont incorporées dans les assemblys, et comment le common language runtime détermine l’équivalence des types COM incorporés.

[Comment : générer des assemblys PIA à l'aide de Tlbimp.exe](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
Décrit comment produire des assemblys PIA à l’aide de *Tlbimp.exe* (importateur de bibliothèques de types).

[Comment : enregistrer des assemblys PIA](how-to-register-primary-interop-assemblies.md)  
Décrit comment inscrire les assemblys PIA avant de les référencer dans vos projets.

[COM Interop sans inscription](registration-free-com-interop.md)  
Décrit comment COM Interop peut activer des composants sans utiliser le Registre Windows.

[Comment : configurer les composants COM .NET Framework pour l'activation sans inscription](configure-net-framework-based-com-components-for-reg.md)  
Décrit comment créer un manifeste d’application, puis explique comment créer et incorporer un manifeste de composant.

## <a name="related-sections"></a>Sections connexes

[Emballages COM](../../standard/native-interop/com-wrappers.md)  
Décrit les wrappers fournis par COM Interop.
