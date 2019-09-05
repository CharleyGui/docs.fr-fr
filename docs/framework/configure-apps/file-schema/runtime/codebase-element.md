---
title: Élément <codeBase>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
ms.openlocfilehash: bd170b817c5ccc337711f8f79968653c29f3eda4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252746"
---
# <a name="codebase-element"></a>\<Élément codebais >

Spécifie où le common language runtime peut trouver un assembly.

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> dependentAssembly**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<codeBase>**

## <a name="syntax"></a>Syntaxe

```xml
   <codeBase
        version="Assembly version"
        href="URL of assembly"/>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`href`|Attribut requis.<br /><br /> Spécifie l’URL où le runtime peut trouver la version spécifiée de l’assembly.|
|`version`|Attribut requis.<br /><br /> Spécifie la version de l’assembly à laquelle s’applique le code base. Le format d’un numéro de version d’assembly est *major. minor. Build. Revision*.|

## <a name="version-attribute"></a>Attribut de version

|Valeur|Description|
|-----------|-----------------|
|Les valeurs valides pour chaque partie du numéro de version sont comprises entre 0 et 65535.|Non applicable.|

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|`buildproviders`|Définit une collection de fournisseurs de générations utilisés pour compiler des fichiers de ressources personnalisés. Le nombre de fournisseurs de générations n'est pas défini.|
|`compilation`|Configure tous les paramètres de compilation utilisés par ASP.NET.|
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|
|`System.web`|Spécifie l'élément racine de la section de configuration ASP.NET.|

## <a name="remarks"></a>Notes

Pour que le runtime utilise le  **\<paramètre CODEBASE >** dans un fichier de configuration machine ou un fichier de stratégie d’éditeur, le fichier doit également rediriger la version de l’assembly. Les fichiers de configuration de l’application peuvent avoir un paramètre code base sans rediriger la version de l’assembly. Après avoir déterminé la version de l’assembly à utiliser, le runtime applique le paramètre de code base du fichier qui détermine la version. Si aucun code base n’est indiqué, le runtime détecte l’assembly de la façon habituelle.

Si l’assembly a un nom fort, le paramètre de code base peut se trouver n’importe où sur l’intranet local ou sur Internet. Si l’assembly est un assembly privé, le paramètre de code base doit être un chemin d’accès relatif au répertoire de l’application.

Pour les assemblys sans nom fort, la version est ignorée et le chargeur utilise la première apparence \<du code base > dans \<le > dependentAssembly. S’il y a une entrée dans le fichier de configuration de l’application qui redirige la liaison vers un autre assembly, la redirection aura la priorité, même si la version de l’assembly ne correspond pas à la demande de liaison.

## <a name="example"></a>Exemples

L’exemple suivant montre comment spécifier où le runtime peut trouver un assembly.

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
         <dependentAssembly>
            <assemblyIdentity name="myAssembly"
                              publicKeyToken="32ab4ba45e0a69a1"
                              culture="neutral" />
            <codeBase version="2.0.0.0"
                      href="http://www.litwareinc.com/myAssembly.dll"/>
         </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
- [Spécification de l'emplacement d'un assembly](../../specify-assembly-location.md)
- [Méthode de localisation des assemblys par le runtime](../../../deployment/how-the-runtime-locates-assemblies.md)
