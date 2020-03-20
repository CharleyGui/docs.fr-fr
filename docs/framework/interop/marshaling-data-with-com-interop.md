---
title: marshaler des données avec COM Interop
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
ms.openlocfilehash: ae41713d5349321725599c0c38d7c6fc515c374b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181374"
---
# <a name="marshaling-data-with-com-interop"></a>marshaler des données avec COM Interop
COM Interop prend en charge l'utilisation des objets COM à partir de code managé, ainsi que l'exposition des objets managés à COM. La prise en charge du marshaling des données vers et depuis COM est complète et fournit quasiment toujours le comportement de marshaling approprié.  
  
 Le SDK Windows comprend les outils d’interopérabilité COM suivants :  
  
- [Importateur de bibliothèques de types (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md), qui convertit une bibliothèque de types COM en un assembly d’interopérabilité. À partir de cet assembly, le service de marshaling d'interopérabilité génère des wrappers qui effectuent le marshaling des données entre la mémoire managée et non managée.  
  
- [Exportateur de bibliothèques de types (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md), qui produit une bibliothèque de types COM à partir d’un assembly et génère un wrapper qui effectue le marshaling lors des appels de méthode.  
  
 Les sections suivantes fournissent des liens vers des rubriques qui décrivent les processus de personnalisation des wrappers d’interopérabilité quand vous pouvez (ou devez) fournir au marshaleur des informations supplémentaires concernant les types.  
  
## <a name="in-this-section"></a>Dans cette section  
[Comment : Créer des emballages manuellement](how-to-create-wrappers-manually.md) Décrit comment créer un emballage COM manuellement dans le code source géré.

 [Comment : migrer DCOM de code managé vers WCF](how-to-migrate-managed-code-dcom-to-wcf.md)  
 Décrit comment migrer du code DCOM managé vers WCF pour obtenir la solution la plus sécurisée.  
  
## <a name="related-sections"></a>Sections connexes  
 [Types de données COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))  
 Fournit les types de données managés et non managés correspondants.  
  
 [Personnalisation des wrappers CCW (COM Callable Wrapper)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))  
 Décrit comment marshaler explicitement des types de données à l’aide de l’attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> au moment du design.  
  
 [Personnaliser des wrappers RCW (Runtime Callable Wrapper)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))  
 Décrit comment ajuster le comportement de marshaling des types dans un assembly d'interopérabilité et comment définir des types COM manuellement.  
  
 [Interopérabilité COM avancée](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))  
 Fournit des liens vers des informations sur l'incorporation de composants COM dans une application .NET Framework.  
  
 [Récapitulatif de la conversion d’un assembly en bibliothèque de types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))  
 Décrit le processus d'exportation et de conversion d'un assembly en une bibliothèque de types.  
  
 [Récapitulatif de la conversion d’une bibliothèque de types en assembly](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))  
 Décrit le processus d'importation et de conversion d'une bibliothèque de types en un assembly.  
  
 [Interopérabilité à l’aide de types génériques](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))  
 Décrit les actions prises en charge lors de l'utilisation de types génériques pour l'interopérabilité COM.
