---
title: "Comment : configurer les composants COM .NET Framework pour l'activation sans inscription"
ms.date: 03/30/2017
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
ms.openlocfilehash: 9e273bd3e4bf2bb6945fe48c850783a54fa9a869
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291753"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a>Comment : configurer les composants COM .NET Framework pour l'activation sans inscription
L’activation sans inscription des composants .NET Framework n’est que légèrement plus compliquée que pour les composants COM. L’installation requiert deux manifestes :  
  
- Les applications COM doivent avoir un manifeste d’application de style Win32 pour identifier le composant managé.  
  
- Les composants .NET Framework doivent avoir un manifeste de composant pour les informations d’activation nécessaires au moment de l’exécution.  
  
 Cette rubrique explique comment associer un manifeste d’application à une application, comment associer un manifeste de composant à un composant et comment incorporer un manifeste de composant dans un assembly.  
  
## <a name="create-an-application-manifest"></a>Créer un manifeste d’application  
  
1. À l’aide d’un éditeur XML, créez (ou modifiez) le manifeste d’application de l’application COM qui interagit avec un ou plusieurs composants managés.  
  
2. Insérez l’en-tête standard suivant au début du fichier :  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
    </assembly>
    ```  
  
     Pour plus d’informations sur les éléments de manifeste et leurs attributs, consultez [Manifestes d’application](/windows/desktop/SbsCs/application-manifests).  
  
3. Identifiez le propriétaire du manifeste. Dans l’exemple suivant, le fichier manifeste appartient à `myComApp` version 1.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myComApp"
                        version="1.0.0.0"
                        processorArchitecture="msil"
      />
    </assembly>  
    ```  
  
4. Identifiez les assemblys dépendants. Dans l’exemple suivant, `myComApp` dépend de `myManagedComp`.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myComApp"
                        version="1.0.0.0"
                        processorArchitecture="x86"
                        publicKeyToken="8275b28176rcbbef"  
      />  
      <dependency>  
        <dependentAssembly>  
          <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myManagedComp"
                        version="6.0.0.0"
                        processorArchitecture="X86"
                        publicKeyToken="8275b28176rcbbef"  
          />  
        </dependentAssembly>  
      </dependency>  
    </assembly>  
    ```  
  
5. Nommez et enregistrez le fichier manifeste. Le nom d’un manifeste d’application est le nom de l’exécutable d’assembly suivi de l’extension .manifest. Par exemple, le nom du fichier manifeste d’application de myComApp.exe est myComApp.exe.manifest.  
  
Vous pouvez installer un manifeste d’application dans le même répertoire que l’application COM. Vous pouvez également l’ajouter en tant que ressource au fichier .exe de l’application. Pour plus d’informations, consultez [à propos des assemblys côte à côte](/windows/desktop/SbsCs/about-side-by-side-assemblies-).  
  
## <a name="create-a-component-manifest"></a>Créer un manifeste de composant  
  
1. À l’aide d’un éditeur XML, créez un manifeste de composant pour décrire l’assembly managé.  
  
2. Insérez l’en-tête standard suivant au début du fichier :  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
    </assembly>
    ```  
  
3. Identifiez le propriétaire du fichier. L’élément `<assemblyIdentity>` de l’élément `<dependentAssembly>` dans le fichier manifeste d’application doit correspondre à celui figurant dans le manifeste de composant. Dans l’exemple suivant, le fichier manifeste appartient à `myManagedComp` version 1.2.3.4.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"  
                        publicKeyToken="8275b28176rcbbef"  
                        processorArchitecture="msil"  
           />
    </assembly>
    ```  
  
4. Identifiez chaque classe dans l’assembly. Utilisez l’élément `<clrClass>` pour identifier de manière unique chaque classe dans l’assembly managé. L’élément, qui est un sous-élément de l’élément `<assembly>`, a les attributs décrits dans le tableau suivant.  
  
    |Attribut|Description|Obligatoire|  
    |---------------|-----------------|--------------|  
    |`clsid`|Identificateur qui spécifie la classe à activer.|Oui|  
    |`description`|Chaîne qui informe l’utilisateur sur le composant. L’attribut par défaut est une chaîne vide.|Non|  
    |`name`|Chaîne représentant la classe managée.|Oui|  
    |`progid`|Identificateur à utiliser pour une activation à liaison tardive.|Non|  
    |`threadingModel`|Modèle de thread COM. "Both" est la valeur par défaut.|Non|  
    |`runtimeVersion`|Spécifie la version du CLR (Common Language Runtime) à utiliser. Si vous ne spécifiez pas cet attribut et que le CLR n’est pas déjà chargé, le composant est chargé avec la version du CLR la plus récente, antérieure à la version CLR 4. Si vous spécifiez v1.0.3705, v1.1.4322 ou v2.0.50727, la version passe automatiquement à la version du CLR installée la plus récente antérieure à la version CLR 4 (habituellement v2.0.50727). Si une autre version du CLR est déjà chargée et que la version spécifiée peut être chargée in-process côte à côte, la version spécifiée est chargée ; sinon, le CLR chargé est utilisé. Cela peut provoquer un échec de chargement.|Non|  
    |`tlbid`|Identificateur de la bibliothèque de types qui contient les informations de type sur la classe.|Non|  
  
     Toutes les balises d’attribut respectent la casse. Vous pouvez obtenir des CLSID, des ProgID, des modèles de thread et la version du runtime en affichant la bibliothèque de types exportée de l’assembly à l’aide de l’explorateur d’objets OLE/COM (Oleview.exe).  
  
     Le manifeste de composant suivant identifie deux classes, `testClass1` et `testClass2`.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"
                        publicKeyToken="8275b28176rcbbef"  
           />  
           <clrClass  
                        clsid="{65722BE6-3449-4628-ABD3-74B6864F9739}"  
                        progid="myManagedComp.testClass1"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass1"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <clrClass  
                        clsid="{367221D6-3559-3328-ABD3-45B6825F9732}"  
                        progid="myManagedComp.testClass2"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass2"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <file name="MyManagedComp.dll">  
           </file>  
    </assembly>  
    ```  
  
5. Nommez et enregistrez le fichier manifeste. Le nom d’un manifeste de composant est le nom de la bibliothèque d’assemblys suivi de l’extension .manifest. Par exemple, le nom de myManagedComp.dll est myManagedComp.manifest.  
  
 Vous devez incorporer le manifeste de composant en tant que ressource dans l’assembly.  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a>Pour incorporer un manifeste de composant dans un assembly managé  
  
1. Créez un script de ressources qui contient l’instruction suivante :  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     Dans cette instruction, `myManagedComp.manifest` est le nom du manifeste de composant incorporé. Pour cet exemple, le nom du fichier de script est `myresource.rc`.  
  
2. Compilez le script à l’aide de l’outil Compilateur de ressources Microsoft Windows (Rc.exe). Saisissez ensuite la commande suivante dans l’invite de commandes :  
  
     `rc myresource.rc`  
  
     Rc.exe génère le fichier de ressources `myresource.res`.  
  
3. Compilez de nouveau le fichier source de l’assembly et spécifiez le fichier de ressources à l’aide de l’option **/win32res** :  
  
    `/win32res:myresource.res`  
  
     Là encore `myresource.res` , est le nom du fichier de ressources contenant des ressources incorporées.  
  
## <a name="see-also"></a>Voir aussi

- [COM Interop sans inscription](registration-free-com-interop.md)
- [Configuration requise pour COM Interop sans inscription](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))
- [Configuration des composants COM pour l’activation sans inscription](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))
- [Activation sans inscription de composants .NET : une procédure pas à pas](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))
