---
title: 'Procédure : créer des wrappers COM'
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4ae9710b99c85cfcbe3de2669c7ee85d0d24ef4
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629335"
---
# <a name="how-to-create-com-wrappers"></a>Procédure : créer des wrappers COM

Vous pouvez créer des wrappers COM (Component Object Model) à l’aide des fonctionnalités Visual Studio 2005 ou des outils .NET Framework Tlbimp.exe et Regasm.exe. Ces deux méthodes génèrent deux types de wrappers COM :

- un [wrapper RCW (Runtime Callable Wrapper)](../../../docs/standard/native-interop/runtime-callable-wrapper.md) d’une bibliothèque de types pour exécuter un objet COM en code managé ;

- un [wrapper CCW (COM Callable Wrapper)](../../../docs/standard/native-interop/com-callable-wrapper.md) avec les paramètres de Registre requis pour exécuter un objet managé dans une application native.

Dans Visual Studio 2005, vous pouvez ajouter le wrapper COM à votre projet en tant que référence.

## <a name="wrap-com-objects-in-a-managed-application"></a>Encapsuler des objets COM dans une application managée

### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a>Pour créer un wrapper RCW à l’aide de Visual Studio

1. Ouvrez le projet pour votre application managée.

2. Dans le menu **Projet**, cliquez sur **Afficher tous les fichiers**.

3. Dans le menu **Projet**, cliquez sur **Ajouter une référence**.

4. Dans la boîte de dialogue Ajouter une référence, cliquez sur l’onglet **COM**, sélectionnez le composant que vous souhaitez utiliser et cliquez sur **OK**.

     Dans l’**Explorateur de solutions**, notez que le composant COM est ajouté au dossier Références dans votre projet.

Vous pouvez maintenant écrire le code pour accéder à l’objet COM. Vous pouvez commencer par déclarer l’objet, par exemple avec une instruction `Imports` pour Visual Basic ou une instruction `Using` pour C#.

> [!NOTE]
> Si vous souhaitez programmer des composants Microsoft Office, installez d’abord les [assemblys PIA (Primary Interop Assembly) de Microsoft Office](https://go.microsoft.com/fwlink/?LinkId=50479) à partir du Centre de téléchargement Microsoft. À l’étape 4, sélectionnez la version la plus récente de la bibliothèque d’objets disponible pour le produit Office que vous voulez, comme la **bibliothèque d’objets Microsoft Word 11.0**.  
  
### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a>Pour créer un wrapper RCW à l’aide des outils .NET Framework  
  
- Exécutez l’outil [Tlbimp.exe (importateur de bibliothèques de types)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).  
  
 Cet outil crée un assembly qui contient des métadonnées de runtime pour les types définis dans la bibliothèque de types d’origine.  
  
## <a name="wrap-managed-objects-in-a-native-application"></a>Encapsuler des objets managés dans une application native  
  
### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a>Pour créer un wrapper CCW à l’aide de Visual Studio  
  
1. Créez un projet de bibliothèque de classes pour la classe managée que vous souhaitez exécuter en code natif. La classe doit avoir un constructeur sans paramètre.  
  
     Vérifiez que vous disposez d’un numéro de version à quatre parties complet pour votre assembly dans le fichier AssemblyInfo. Ce numéro est requis pour assurer le contrôle de version dans le Registre Windows. Pour plus d’informations sur les numéros de version, consultez [Contrôle de version des assemblys](../../../docs/framework/app-domains/assembly-versioning.md).  
  
2. Dans le menu **Projet**, cliquez sur **Propriétés**.  
  
3. Cliquez sur l’onglet **Compiler**.  
  
4. Cochez la case **Inscrire pour COM Interop**.  
  
 Quand vous générez le projet, l’assembly est automatiquement inscrit pour COM Interop. Si vous générez une application native dans Visual Studio 2005, vous pouvez utiliser l’assembly en cliquant sur **Ajouter une référence** dans le menu **Projet**.  
  
### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a>Pour créer un wrapper CCW à l’aide des outils .NET Framework  
  
Exécutez l’outil [Regasm.exe (outil d’inscription d’assemblys)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md).  
  
Cet outil lit les métadonnées de l’assembly et ajoute les entrées nécessaires au Registre. Par conséquent, les clients COM peuvent créer des classes .NET Framework en toute transparence. Vous pouvez utiliser l’assembly comme s’il s’agissait d’une classe COM native.  
  
Vous pouvez exécuter Regasm.exe sur un assembly situé dans n’importe quel répertoire, puis [Gacutil.exe (outil Global Assembly Cache)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) pour le déplacer dans le Global Assembly Cache. Le déplacement de l’assembly n’invalide pas les entrées du Registre d’emplacement, car le Global Assembly Cache est toujours examiné si l’assembly est introuvable ailleurs.  
  
## <a name="see-also"></a>Voir aussi

- [Wrapper pouvant être appelé par le runtime](../../../docs/standard/native-interop/runtime-callable-wrapper.md)
- [Wrapper CCW (COM Callable Wrapper)](../../../docs/standard/native-interop/com-callable-wrapper.md)
