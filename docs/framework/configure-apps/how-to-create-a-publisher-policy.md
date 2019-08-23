---
title: 'Procédure : Créer une stratégie d’éditeur'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: bf5b55eb01a31106fcc7cb0d79212416ab0c898d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913048"
---
# <a name="how-to-create-a-publisher-policy"></a>Procédure : Créer une stratégie d’éditeur
Les fournisseurs d’assemblys peuvent indiquer que les applications doivent utiliser une version plus récente d’un assembly en incluant un fichier de stratégie d’éditeur avec l’assembly mis à niveau. Le fichier de stratégie d’éditeur spécifie la redirection d’assembly et les paramètres de base de code, et utilise le même format qu’un fichier de configuration d’application. Le fichier de stratégie d’éditeur est compilé dans un assembly et placé dans le Global Assembly Cache.  
  
 La création d’une stratégie d’éditeur implique trois étapes:  
  
1. Créez un fichier de stratégie d’éditeur.  
  
2. Créer un assembly de stratégie d’éditeur.  
  
3. Ajoutez l’assembly de stratégie d’éditeur au Global Assembly Cache.  
  
 Le schéma de la stratégie d’éditeur est décrit dans redirection des [versions](redirect-assembly-versions.md)d’assembly. L’exemple suivant montre un fichier de stratégie d’éditeur qui redirige une version `myAssembly` de vers une autre.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <!-- Redirecting to version 2.0.0.0 of the assembly. -->  
         <bindingRedirect oldVersion="1.0.0.0"  
                          newVersion="2.0.0.0"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 Pour savoir comment spécifier une base de code, consultez [spécification de l’emplacement d'](specify-assembly-location.md)un assembly.  
  
## <a name="creating-the-publisher-policy-assembly"></a>Création de l’assembly de stratégie d’éditeur  
 Utilisez [Assembly Linker (al. exe)](../tools/al-exe-assembly-linker.md) pour créer l’assembly de stratégie d’éditeur.  
  
#### <a name="to-create-a-publisher-policy-assembly"></a>Pour créer un assembly de stratégie d’éditeur  
  
1. À l’invite de commandes, tapez la commande suivante:  
  
     **al/Link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *keyPairFile* **/Platform:** *ProcessorArchitecture*  
  
     Dans cette commande:  
  
    - L’argument *publisherPolicyFile* est le nom du fichier de stratégie d’éditeur.  
  
    - L’argument *publisherPolicyAssemblyFile* est le nom de l’assembly de stratégie d’éditeur qui résulte de cette commande. Le nom du fichier de l’assembly doit respecter le format suivant:  
  
         **renvoi.** *majorNumber* **.** *minorNumber* **.** *mainAssemblyName* **.dll**  
  
    - L’argument *keyPairFile* est le nom du fichier contenant la paire de clés. Vous devez signer l’assembly et l’assembly de stratégie d’éditeur avec la même paire de clés.  
  
    - L’argument *ProcessorArchitecture* identifie la plateforme ciblée par un assembly spécifique au processeur.  
  
        > [!NOTE]
        >  La possibilité de cibler une architecture de processeur spécifique est une nouveauté de la version 2,0 de .NET Framework.  
  
     La commande suivante crée un assembly de stratégie `policy.1.0.myAssembly` d’éditeur appelé à partir d' `pub.config`un fichier de stratégie d’éditeur appelé, assigne un nom fort à l' `sgKey.snk` assembly à l’aide de la paire de clés dans le fichier et spécifie que l’assembly cible le x86 architecture du processeur.  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     L’assembly de stratégie d’éditeur doit correspondre à l’architecture de processeur de l’assembly auquel il s’applique. Ainsi, si votre assembly a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> la <xref:System.Reflection.ProcessorArchitecture.MSIL>valeur, l’assembly de stratégie d’éditeur de cet assembly `/platform:anycpu`doit être créé avec. Vous devez fournir un assembly de stratégie d’éditeur distinct pour chaque assembly spécifique au processeur.  
  
     Une conséquence de cette règle est que pour modifier l’architecture de processeur d’un assembly, vous devez modifier le composant principal ou mineur du numéro de version, afin de pouvoir fournir un nouvel assembly de stratégie d’éditeur avec l’architecture de processeur correcte. L’ancien assembly de stratégie d’éditeur ne peut pas traiter votre assembly une fois que votre assembly a une architecture de processeur différente.  
  
     Une autre conséquence est que l’éditeur de liens version 2,0 ne peut pas être utilisé pour créer un assembly de stratégie d’éditeur pour un assembly compilé à l’aide de versions antérieures du .NET Framework, car il spécifie toujours l’architecture du processeur.  
  
## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Ajout de l’assembly de stratégie d’éditeur au global assembly cache  
 Utilisez l' [outil global assembly cache (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) pour ajouter l’assembly de stratégie d’éditeur au global assembly cache.  
  
#### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Pour ajouter l’assembly de stratégie d’éditeur au Global Assembly Cache  
  
1. À l’invite de commandes, tapez la commande suivante:  
  
     **gacutil /i**  *publisherPolicyAssemblyFile*  
  
     La commande suivante ajoute `policy.1.0.myAssembly.dll` à la global assembly cache.  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  L’assembly de stratégie d’éditeur ne peut pas être ajouté au Global Assembly Cache, sauf si le fichier de stratégie d’éditeur d’origine se trouve dans le même répertoire que l’assembly.  
  
## <a name="see-also"></a>Voir aussi

- [Programmation à l’aide d’assemblys](../app-domains/programming-with-assemblies.md)
- [Méthode de localisation des assemblys par le runtime](../deployment/how-the-runtime-locates-assemblies.md)
- [Configuration d’applications à l’aide de fichiers de configuration](index.md)
- [Schéma des paramètres d’exécution](./file-schema/runtime/index.md)
- [Schéma des fichiers de configuration](./file-schema/index.md)
- [Redirection des versions d'assemblys](redirect-assembly-versions.md)
