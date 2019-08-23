---
title: Élément <loadFromRemoteSources>
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2268d07fb643621c944ef9bf561156b5332aaafc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920719"
---
# <a name="loadfromremotesources-element"></a>\<loadFromRemoteSources >, élément
Spécifie si les assemblys chargés à partir de sources distantes doivent bénéficier d’une confiance totale dans .NET Framework 4 et versions ultérieures.
  
> [!NOTE]
> Si vous êtes redirigé vers cet article en raison d’un message d’erreur dans la liste d’erreurs d’un projet Visual Studio [ou d’une erreur de génération, consultez Procédure: Utilisez un assembly à partir du Web dans](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100))Visual Studio.  
  
 \<configuration>  
\<runtime>  
\<loadFromRemoteSources>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si un assembly qui est chargé à partir d’une source distante doit bénéficier d’une confiance totale.|  
  
## <a name="enabled-attribute"></a>attribut activé  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|N’accordez pas une confiance totale aux applications à partir de sources distantes. Il s'agit de la valeur par défaut.|  
|`true`|Accordez une confiance totale aux applications à partir de sources distantes.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## <a name="remarks"></a>Notes

Dans le .NET Framework 3,5 et les versions antérieures, si vous chargez un assembly à partir d’un emplacement distant, le code de l’assembly s’exécute en confiance partielle avec un jeu d’autorisations qui dépend de la zone à partir de laquelle il est chargé. Par exemple, si vous chargez un assembly à partir d’un site Web, il est chargé dans la zone Internet et reçoit le jeu d’autorisations Internet. En d’autres termes, il s’exécute dans un bac à sable (sandbox) Internet.

À partir du .NET Framework 4, la stratégie de sécurité d’accès du code est désactivée et les assemblys sont chargés en confiance totale. En règle générale, cela accorde une confiance totale aux assemblys chargés avec <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> la méthode qui avait précédemment été bac à sable (sandbox). Pour éviter cela, la possibilité d’exécuter du code dans des assemblys chargés à partir d’une source distante est désactivée par défaut. Par défaut, si vous tentez de charger un assembly distant <xref:System.IO.FileLoadException> , un avec un message d’exception semblable au suivant est levé:

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported. 
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' ---> 
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly 
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default, 
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch. 
```

Pour charger l’assembly et exécuter son code, vous devez:

- Créez explicitement un bac à sable (sandbox) [pour l’assembly (consultez Procédure: Exécuter du code de confiance partielle dans](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)un bac à sable (sandbox)).

- Exécutez le code de l’assembly en confiance totale. Pour ce faire, vous devez configurer `<loadFromRemoteSources>` l’élément. Elle vous permet de spécifier que les assemblys qui s’exécutent en mode de confiance partielle dans les versions antérieures du .NET Framework désormais s’exécuter avec une confiance totale dans le .NET Framework 4 et versions ultérieures.

> [!IMPORTANT]
> Si l’assembly ne doit pas s’exécuter en mode de confiance totale, ne définissez pas cet élément de configuration. Au lieu de cela, créez <xref:System.AppDomain> un bac à sable (sandbox) dans lequel charger l’assembly.

L' `enabled` attribut de l' `<loadFromRemoteSources>` élément est effectif uniquement lorsque la sécurité d’accès du code (cas) est désactivée. Par défaut, la stratégie CAS est désactivée dans le .NET Framework 4 et versions ultérieures. Si vous `enabled` affectez `true`à, les assemblys distants bénéficient d’une confiance totale.

Si `enabled` n’a pas la `true`valeur, <xref:System.IO.FileLoadException> une exception est levée dans l’une des conditions suivantes:

- Le comportement de bac à sable (sandbox) du domaine actuel est différent de son comportement dans le .NET Framework 3,5. Cela nécessite que la stratégie CAS soit désactivée et que le domaine actuel ne soit pas en mode bac à sable (sandbox).

- L’assembly en cours de chargement ne `MyComputer` provient pas de la zone.

La définition `<loadFromRemoteSources>` de l' `true` élément pour empêche la levée de cette exception. Elle vous permet de spécifier que vous ne comptez pas sur les common language runtime pour mettre en sandbox les assemblys chargés pour la sécurité, et qu’ils peuvent être autorisés à s’exécuter en mode confiance totale.

## <a name="notes"></a>Notes

- Dans le .NET Framework 4,5 et versions ultérieures, les assemblys sur les partages réseau locaux s’exécutent en mode de confiance totale par défaut; vous n’avez pas besoin d’activer `<loadFromRemoteSources>` l’élément.

- Si une application a été copiée à partir du Web, elle est marquée par Windows comme étant une application Web, même si elle réside sur l’ordinateur local. Vous pouvez modifier cette désignation en modifiant ses propriétés de fichier, ou vous pouvez utiliser `<loadFromRemoteSources>` l’élément pour accorder la confiance totale à l’assembly. Vous pouvez également utiliser la <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> méthode pour charger un assembly local que le système d’exploitation a marqué comme ayant été chargé à partir du Web.

- Vous pouvez obtenir un <xref:System.IO.FileLoadException> dans une application qui s’exécute dans une application Windows Virtual PC. Cela peut se produire lorsque vous essayez de charger un fichier à partir de dossiers liés sur l’ordinateur hôte. Cela peut également se produire lorsque vous essayez de charger un fichier à partir d’un dossier lié à [services Bureau à distance](https://go.microsoft.com/fwlink/?LinkId=182775) (services Terminal Server). Pour éviter l’exception, affectez `true`à la valeur `enabled` .

## <a name="configuration-file"></a>fichier de configuration

Cet élément est généralement utilisé dans le fichier de configuration de l’application, mais peut être utilisé dans d’autres fichiers de configuration en fonction du contexte. Pour plus d’informations, consultez l’article [utilisations plus implicites de la stratégie cas: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839) dans le blog sur la sécurité .net.  

## <a name="example"></a>Exemple

L’exemple suivant montre comment accorder une confiance totale aux assemblys chargés à partir de sources distantes.

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a>Voir aussi

- [Utilisations plus implicites de la stratégie CAS: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839)
- [Guide pratique pour exécuter du code d’un niveau de confiance partiel dans un bac à sable (sandbox)](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
