---
title: Exécution côte à côte dans .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution
ms.assetid: 649f1342-766b-49e6-a90d-5b019a751e11
ms.openlocfilehash: e965702943149d3ed34be39bb2923ad52dcf90ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181645"
---
# <a name="side-by-side-execution-in-the-net-framework"></a>Exécution côte à côte dans .NET Framework

L'exécution côte à côte désigne la possibilité d'exécuter plusieurs versions d'une application ou d'un composant sur le même ordinateur. Vous pouvez avoir plusieurs versions du Common Language Runtime et plusieurs versions d'applications et de composants qui utilisent une version du runtime sur le même ordinateur simultanément.  
  
L'illustration suivante montre l'utilisation par plusieurs applications de deux versions différentes du runtime sur le même ordinateur. Les applications A, B et C utilisent la version 1.0 du runtime, l'application D utilise la version 1.1 du runtime.  
  
![Exécution côte à côte de différentes versions du runtime](./media/side-by-side-execution/side-by-side-runtime-execution.gif)  
  
Le .NET Framework se compose du Common Language Runtime et d’une collection d’assemblys qui contiennent les types d’API. Le runtime et les assemblys .NET Framework sont gérés séparément. Par exemple, la version 4.0 du runtime correspond en fait à la version 4.0.319, tandis que la version 1.0 des assemblys .NET Framework correspond à la version 1.0.3300.0.  
  
L'illustration suivante montre l'utilisation par plusieurs applications de deux versions différentes d'un composant sur le même ordinateur. Les applications A et B utilisent la version 1.0 du composant, l'application C utilise la version 2.0 du même composant.  
  
![Diagramme qui montre l’exécution côte à côte d’un composant.](./media/side-by-side-execution/side-by-side-component-execution.gif)  
  
L'exécution côte à côte vous donne davantage de contrôle sur les versions d'un composant auxquelles se lie une application ainsi que sur la version du runtime utilisée par une application.  
  
## <a name="benefits-of-side-by-side-execution"></a>Avantages de l'exécution côte à côte  

Avant Windows XP et le .NET Framework, les conflits de DLL se produisaient, car les applications étaient incapables de faire la distinction entre les versions incompatibles du même code. Les informations de type contenues dans une DLL étaient liées uniquement à un nom de fichier. Une application ne disposait d'aucun moyen pour déterminer si les types contenus dans une DLL correspondaient aux mêmes types ayant servi à générer l'application. En conséquence, la nouvelle version d'un composant risquait de remplacer l'ancienne version et de provoquer l'interruption des applications.  
  
L'exécution côte à côte et le .NET Framework fournissent les fonctionnalités suivantes permettant d'éliminer les conflits de DLL :  
  
- Assemblys avec nom fort.  
  
     L'exécution côte à côte utilise des assemblys avec nom fort pour lier des informations de type à une version spécifique d'un assembly. Cela permet d'éviter la liaison d'une application ou d'un composant à une version non valide d'un assembly. Les assemblys avec nom fort permettent également à plusieurs versions d'un fichier de se trouver sur le même ordinateur et d'être utilisé par des applications. Pour plus d’informations, consultez [Assemblys avec nom fort](../../standard/assembly/strong-named.md).  
  
- Stockage de code prenant en compte la version.  
  
     Le .NET Framework permet le stockage de code prenant en compte la version dans le Global Assembly Cache. Le Global Assembly Cache est un cache de code à l'échelle de l'ordinateur présent sur tous les ordinateurs où est installé le .NET Framework. Il stocke des assemblys basés sur les informations de version, de culture et de l'éditeur et prend en charge plusieurs versions de composants et d'applications. Pour plus d’informations, consultez [Global Assembly Cache](../app-domains/gac.md).  
  
- Isolement :  
  
     À l'aide du .NET Framework, vous pouvez créer des applications et des composants qui s'exécutent de manière isolée. L'isolement est une fonctionnalité essentielle de l'exécution côte à côte. Elle implique la connaissance des ressources que vous utilisez et le partage de celles-ci en toute confiance entre plusieurs versions d'une application ou d'un composant. L'isolement comprend également le stockage de fichiers d'une façon spécifique à la version. Pour plus d’informations sur l’isolation, consultez [Recommandations en matière de création de composants pour l’exécution côte à côte](guidelines-for-creating-components-for-side-by-side-execution.md).  
  
## <a name="version-compatibility"></a>Compatibilité des versions  

Les versions 1.0 et 1.1 du .NET Framework sont conçues pour être compatibles. Une application générée avec le .NET Framework version 1.0 doit s'exécuter sur la version 1.1 et une application générée avec le .NET Framework version 1.1 doit s'exécuter sur la version 1.0. Notez toutefois que les fonctionnalités API ajoutées dans la version 1.1 du .NET Framework ne fonctionnent pas avec la version 1.0 du .NET Framework. Les applications créées avec la version 2.0 s'exécuteront uniquement sur la version 2.0. Les applications de la version 2.0 ne pourront pas être utilisées avec la version 1.1 ou avec les versions antérieures.  
  
Les versions du .NET Framework sont traitées en tant que bloc unique comportant le runtime et les assemblys .NET Framework associés (un concept appelé unification d'assemblys). Vous pouvez rediriger la liaison d'assembly pour inclure d'autres versions des assemblys .NET Framework. Toutefois, substituer la liaison d'assembly par défaut présente des risques et doit faire l'objet de tests rigoureux avant déploiement.  
  
## <a name="locating-runtime-version-information"></a>Localisation des informations de version du runtime  

Les informations de version du runtime utilisées pour la compilation d'une application ou d'un composant ainsi que les versions du runtime nécessaires à l'exécution de l'application sont stockées dans deux emplacements. Lors de la compilation d'une application ou d'un composant, les informations de version du runtime utilisées pour la compilation sont stockées dans l'exécutable managé. Les informations sur les versions du runtime nécessaires à l'application ou au composant sont stockées dans le fichier de configuration de l'application.  
  
### <a name="runtime-version-information-in-the-managed-executable"></a>Informations de version du runtime dans l'exécutable managé  

L'en-tête du fichier exécutable portable (PE) de chaque application et composant managé contient des informations sur la version du runtime utilisée pour sa création. Le common language runtime utilise ces informations pour déterminer la version du runtime la plus appropriée à exécuter par l'application.  
  
### <a name="runtime-version-information-in-the-application-configuration-file"></a>Informations de version du runtime dans le fichier de configuration de l'application  

En plus des informations fournies dans l'en-tête du fichier PE, une application peut être déployée avec un fichier de configuration qui fournit des informations de version du runtime. Le fichier de configuration d'application est un fichier XML créé par le développeur de l'application et livré avec l'application. Le [ \<dépassement requis> Élément](../configure-apps/file-schema/startup/requiredruntime-element.md) de la [ \<section start-up>](../configure-apps/file-schema/startup/startup-element.md), s’il est présent dans ce fichier, précise quelles versions de l’heure d’exécution et quelles versions d’un composant l’application prend en charge. Vous pouvez également utiliser ce fichier à des fins de test pour vérifier la compatibilité de l'application avec différentes versions du runtime.  
  
Le runtime peut aussi utiliser un fichier de configuration de l'application pour interagir avec du code non managé, y compris des applications COM et COM+. Le fichier de configuration de l'application s'applique à l'ensemble du code managé que vous activez par l'intermédiaire de COM. Il peut spécifier les versions du runtime qu'il prend en charge ainsi que les redirections d'assemblys. Par défaut, les applications COM Interop qui appellent du code managé utilisent la version du runtime la plus récente installée sur l'ordinateur.  
  
 Pour plus d’informations sur les fichiers de configuration de l’application, consultez [Configuration des applications](../configure-apps/index.md).  
  
## <a name="determining-which-version-of-the-runtime-to-load"></a>Détermination de la version du runtime à charger  

Le common language runtime se sert des informations suivantes pour déterminer la version du runtime à charger pour une application :  
  
- Les versions du runtime disponibles  
  
- Les versions du runtime prises en charge par l'application  
  
### <a name="supported-runtime-versions"></a>Versions du runtime prises en charge  

Le runtime se base sur le fichier de configuration de l'application et l'en-tête du fichier exécutable portable (PE) pour déterminer la version du runtime prise en charge par l'application. En l'absence de fichier de configuration de l'application, le runtime charge la version du runtime qui est spécifiée dans l'en-tête du fichier PE de l'application (si cette version est disponible).  
  
S'il existe un fichier de configuration de l'application, le runtime détermine la version appropriée du runtime à charger à partir des résultats du processus suivant :  
  
1. Le temps d’exécution examine l’élément [ \<d’élément de> d’arrêt](../configure-apps/file-schema/startup/supportedruntime-element.md) supporté dans le fichier de configuration d’application. Si une ou plusieurs des versions de temps d’exécution prises en charge spécifiées dans ** \<l’élément de>deruntime pris** en charge sont présentes, le temps d’exécution charge la version de temps d’exécution spécifiée par le premier ** \<élément de>SupportRuntime.** Si cette version n’est pas disponible, l’exécution examine l’élément ** \<de>de prise en charge** suivant et tente de charger la version de durée spécifiée. Si cette version de temps d’exécution n’est pas disponible, les éléments ** \<>de prise en charge** ultérieures sont examinés. Si aucune des versions du runtime prises en charge n'est disponible, le runtime ne peut pas charger de version du runtime et affiche un message à l'utilisateur (voir l'étape 3).  
  
2. Le runtime lit l'en-tête du fichier PE du fichier exécutable de l'application. Si la version du runtime spécifiée par l'en-tête du fichier PE est disponible, le runtime la charge. Sinon, le runtime recherche une version du runtime que Microsoft a déterminé comme compatible avec la version du runtime spécifiée dans l'en-tête du fichier PE. Si cette version est introuvable, le processus continue jusqu'à l'étape 3.  
  
3. Le runtime affiche un message indiquant que la version du runtime prise en charge par l'application n'est pas disponible. Le runtime n'est pas chargé.  
  
    > [!NOTE]
    > Vous pouvez désactiver l’affichage de ce message en définissant la valeur NoGuiFromShim sous la clé de Registre HKLM\Software\Microsoft\\.NETFramework ou en utilisant la variable d’environnement COMPLUS_NoGuiFromShim. Par exemple, vous pouvez désactiver le message pour des applications qui n'interagissent généralement pas avec l'utilisateur, telles que des installations sans assistance ou des services Windows. Si l'affichage de ce message est désactivé, le runtime écrit un message dans le journal des événements.  Définissez la valeur de Registre NoGuiFromShim à 1 si vous voulez désactiver ce message pour toutes les applications d'un ordinateur. Vous pouvez aussi définir la variable d'environnement COMPLUS_NoGuiFromShim à la valeur 1 pour désactiver le message pour des applications s'exécutant dans un contexte utilisateur particulier.  
  
> [!NOTE]
> Après le chargement d'une version du runtime, les redirections de liaison d'assembly peuvent spécifier qu'une version différente d'un assembly .NET Framework donné soit chargée. Ces redirections de liaison s'appliquent uniquement à l'assembly spécifique qui fait l'objet de la redirection.  
  
## <a name="partially-qualified-assembly-names-and-side-by-side-execution"></a>Exécution côte à côte et noms d'assembly partiellement qualifiés  

Du fait qu'elles représentent une source potentielle de problèmes pour l'exécution côte à côte, les références d'assembly partiellement qualifiées ne peuvent s'utiliser que pour les liaisons à des assemblys au sein du répertoire d'une application. Dans la mesure du possible, n'utilisez pas de références d'assembly partiellement qualifiées dans votre code.  
  
Pour atténuer les références d’assemblage partiellement qualifiées dans le code, vous pouvez utiliser [ \<l’élément qualifieAssembly>](../configure-apps/file-schema/runtime/qualifyassembly-element.md) dans un fichier de configuration d’application pour qualifier pleinement les références d’assemblage partiellement qualifiées qui se produisent dans le code. Utilisez ** \<l’élément qualifieAssembly>** pour spécifier uniquement les champs qui n’ont pas été définis dans la référence partielle. L’identité de l’assembly indiquée dans l’attribut **fullName** doit contenir toutes les informations nécessaires pour qualifier l’assembly avec un nom complet : le nom de l’assembly, la clé publique, la culture et la version.  
  
 L'exemple suivant illustre l'entrée du fichier de configuration de l'application qui permet de qualifier un assembly nommé `myAssembly` avec un nom complet.  
  
```xml  
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
<qualifyAssembly partialName="myAssembly"
fullName="myAssembly,  
      version=1.0.0.0,
publicKeyToken=...,
      culture=neutral"/>
</assemblyBinding>
```  
  
 Chaque fois qu'une instruction de chargement d'un assembly fait référence à `myAssembly`, les paramètres du fichier de configuration entraînent la conversion automatique par le runtime de la référence partiellement qualifiée `myAssembly` en une référence qualifiée complète. Par exemple, Assembly.Load("myAssembly") devient Assembly.Load("myAssembly, version=1.0.0.0, publicKeyToken=..., culture=neutral").  
  
> [!NOTE]
> Vous pouvez utiliser la méthode **LoadWithPartialName** pour ignorer la restriction du common language runtime qui n’autorise pas le chargement des assemblys partiellement référencés à partir du Global Assembly Cache. Cette méthode est réservée aux scénarios de communication à distance, car elle génère souvent des problèmes dans l'exécution côte à côte.  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Intitulé|Description|  
|-----------|-----------------|  
|[Comment : activer et désactiver la redirection de liaison automatique](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)|Explique comment lier une application à une version spécifique d'un assembly.|  
|[Configuration de la redirection de liaison d’assembly](configuring-assembly-binding-redirection.md)|Explique comment rediriger les références de liaison d’assembly vers une version spécifique des assemblys du .NET Framework.|  
|[Exécution côte à côte in-process](in-process-side-by-side-execution.md)|Explique comment utiliser l'activation d'hôte du runtime côte à côte in-process pour exécuter plusieurs versions du CLR dans un même processus.|  
|[Assemblys dans .NET](../../standard/assembly/index.md)|Fournit une vue d'ensemble conceptuelle des assemblys.|  
|[Domaines d'application](../app-domains/application-domains.md)|Fournit une vue d'ensemble conceptuelle des domaines d'application.|  
  
## <a name="reference"></a>Informations de référence  

[\<supportedRuntime> Element](../configure-apps/file-schema/startup/supportedruntime-element.md)
