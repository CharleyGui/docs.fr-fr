---
title: Inscription d'assemblys dans COM
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, registering assemblies
- unregistering assemblies
- interoperation with unmanaged code, registering assemblies
- registering assemblies
ms.assetid: 87925795-a3ae-4833-b138-125413478551
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6482d5fa046409d15913ea26300d298238750326
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648555"
---
# <a name="registering-assemblies-with-com"></a>Inscription d'assemblys dans COM
Vous pouvez exécuter l’outil en ligne de commande [Assembly Registration Tool (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) pour inscrire ou désinscrire un assembly à utiliser avec COM. Regasm.exe ajoute des informations sur la classe au Registre système pour que les clients COM puissent utiliser la classe .NET Framework en toute transparence. La classe <xref:System.Runtime.InteropServices.RegistrationServices> fournit des fonctionnalités équivalentes.  
  
 Pour activer un composant managé à partir d’un client COM, vous devez d’abord l’inscrire dans le Registre Windows. Le tableau suivant montre les clés que Regasm.exe ajoute généralement au Registre Windows (000000 indique la valeur GUID).  
  
|GUID|Description|Clé du Registre|  
|----------|-----------------|------------------|  
|CLSID|Identificateur de classe|HKEY_CLASSES_ROOT\CLSID\\{000…000}|  
|IID|Identificateur d’interface|HKEY_CLASSES_ROOT\Interface\\{000…000}|  
|LIBID|Identificateur de bibliothèque|HKEY_CLASSES_ROOT\TypeLib\\{000…000}|  
|ProgID|Identificateur programmatique|HKEY_CLASSES_ROOT\000…000|  
  
 Sous la clé HKCR\CLSID\\{0000…0000}, la valeur par défaut est définie sur le ProgID de la classe, et deux nouvelles valeurs nommées, Class et Assembly, sont ajoutées. Le runtime lit la valeur Assembly à partir du Registre et la passe au service de résolution d’assembly du runtime. Le service de résolution d’assembly tente de localiser l’assembly, en se basant sur son nom et son numéro de version. Pour que le service de résolution d’assembly puisse localiser un assembly, celui-ci doit se trouver dans l’un des emplacements suivants :  
  
- Le Global Assembly Cache (il doit s’agir d’un assembly avec un nom fort)  
  
- Le répertoire de l’application. Les assemblys chargés à partir du chemin d’une application ne sont accessibles qu’à partir de cette application.  
  
- Sur un chemin de fichier spécifié avec l’option **/codebase** définie sur Regasm.exe.  
  
 Regasm.exe crée également la clé InProcServer32 sous la clé HKCR\CLSID\\{0000…0000}. La valeur par défaut de la clé est définie sur le nom de la DLL qui initialise le common language runtime (Mscoree.dll).  
  
## <a name="examining-registry-entries"></a>Examen des entrées du Registre  
 COM Interop fournit une implémentation de fabrique de classe standard permettant de créer une instance de n’importe quelle classe .NET Framework. Les clients peuvent appeler **DllGetClassObject** dans la DLL managée pour obtenir une fabrique de classe et créer des objets, comme ils le feraient avec tout autre composant COM.  
  
 Pour la sous-clé `InprocServer32`, une référence à Mscoree.dll s’affiche (au lieu d’une bibliothèque de types COM traditionnelle) pour indiquer que le common language runtime crée l’objet managé.  
  
## <a name="see-also"></a>Voir aussi

- [Exposition de composants .NET Framework à COM](exposing-dotnet-components-to-com.md)
- [Guide pratique pour référencer des types .NET à partir de COM](how-to-reference-net-types-from-com.md)
- [Appel d’un objet .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))
- [Déploiement d’une application pour accéder à COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))
