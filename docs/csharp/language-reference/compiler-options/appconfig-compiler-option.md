---
title: -appconfig (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
ms.openlocfilehash: 7a7e8e61f65704a2e99385a1be320048d950324c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69922521"
---
# <a name="-appconfig-c-compiler-options"></a><span data-ttu-id="1624f-102">-appconfig (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="1624f-102">-appconfig (C# Compiler Options)</span></span>
<span data-ttu-id="1624f-103">L’option du compilateur **-appconfig** permet à une application C# d’indiquer l’emplacement du fichier de configuration de l’application (app.config) d’un assembly au CLR (Common Language Runtime) au moment de la liaison de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="1624f-103">The **-appconfig** compiler option enables a C# application to specify the location of an assembly's application configuration (app.config) file to the common language runtime (CLR) at assembly binding time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1624f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1624f-104">Syntax</span></span>  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="1624f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1624f-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="1624f-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1624f-106">Required.</span></span> <span data-ttu-id="1624f-107">Fichier de configuration de l’application qui contient des paramètres de liaison de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="1624f-107">The application configuration file that contains assembly binding settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1624f-108">Notes </span><span class="sxs-lookup"><span data-stu-id="1624f-108">Remarks</span></span>  
 <span data-ttu-id="1624f-109">**-appconfig** est notamment utilisé dans des scénarios avancés dans lesquels un assembly doit simultanément référencer à la fois la version du .NET Framework et la version du .NET Framework pour Silverlight d’un assembly de référence particulier.</span><span class="sxs-lookup"><span data-stu-id="1624f-109">One use of **-appconfig** is advanced scenarios in which an assembly has to reference both the .NET Framework version and the .NET Framework for Silverlight version of a particular reference assembly at the same time.</span></span> <span data-ttu-id="1624f-110">Par exemple, un concepteur XAML écrit dans WPF (Windows Presentation Foundation) devra peut-être référencer à la fois le bureau WPF pour l’interface utilisateur du concepteur et le sous-ensemble de WPF qui est fourni avec Silverlight.</span><span class="sxs-lookup"><span data-stu-id="1624f-110">For example, a XAML designer written in Windows Presentation Foundation (WPF) might have to reference both the WPF Desktop, for the designer's user interface, and the subset of WPF that is included with Silverlight.</span></span> <span data-ttu-id="1624f-111">Le même assembly de concepteur doit accéder aux deux assemblys.</span><span class="sxs-lookup"><span data-stu-id="1624f-111">The same designer assembly has to access both assemblies.</span></span> <span data-ttu-id="1624f-112">Par défaut, les références séparées provoquent une erreur du compilateur parce que la liaison d’assembly considère les deux assemblys comme équivalents.</span><span class="sxs-lookup"><span data-stu-id="1624f-112">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span>  
  
 <span data-ttu-id="1624f-113">L’option du compilateur **-appconfig** vous permet de spécifier l’emplacement d’un fichier app.config qui désactive le comportement par défaut à l’aide d’une balise `<supportPortability>`, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="1624f-113">The **-appconfig** compiler option enables you to specify the location of an app.config file that disables the default behavior by using a `<supportPortability>` tag, as shown in the following example.</span></span>  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 <span data-ttu-id="1624f-114">Le compilateur passe l’emplacement du fichier à la logique de liaison d’assembly du CLR.</span><span class="sxs-lookup"><span data-stu-id="1624f-114">The compiler passes the location of the file to the CLR's assembly-binding logic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1624f-115">Si vous utilisez MSBuild (Microsoft Build Engine) pour générer votre application, vous pouvez définir l’option du compilateur **-appconfig** en ajoutant une balise de propriété au fichier .csproj.</span><span class="sxs-lookup"><span data-stu-id="1624f-115">If you are using the Microsoft Build Engine (MSBuild) to build your application, you can set the **-appconfig** compiler option by adding a property tag to the .csproj file.</span></span> <span data-ttu-id="1624f-116">Pour utiliser le fichier app.config qui est déjà défini dans le projet, ajoutez la balise de propriété `<UseAppConfigForCompiler>` au fichier .csproj et affectez-lui la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="1624f-116">To use the app.config file that is already set in the project, add property tag `<UseAppConfigForCompiler>` to the .csproj file and set its value to `true`.</span></span> <span data-ttu-id="1624f-117">Pour spécifier un autre fichier app.config, ajoutez la balise de propriété `<AppConfigForCompiler>` et définissez sa valeur sur l’emplacement du fichier.</span><span class="sxs-lookup"><span data-stu-id="1624f-117">To specify a different app.config file, add property tag `<AppConfigForCompiler>` and set its value to the location of the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1624f-118"> Exemple</span><span class="sxs-lookup"><span data-stu-id="1624f-118">Example</span></span>  
 <span data-ttu-id="1624f-119">L’exemple suivant affiche un fichier app.config qui permet à une application d’avoir des références à la fois à l’implémentation .NET Framework et à l’implémentation .NET Framework pour Silverlight de tout assembly .NET Framework qui existe dans les deux implémentations.</span><span class="sxs-lookup"><span data-stu-id="1624f-119">The following example shows an app.config file that enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="1624f-120">L’option du compilateur **-appconfig** spécifie l’emplacement de ce fichier app.config.</span><span class="sxs-lookup"><span data-stu-id="1624f-120">The **-appconfig** compiler option specifies the location of this app.config file.</span></span>  
  
```xml  
<configuration>  
      <runtime>  
      <assemblyBinding>  
            <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
            <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
      </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1624f-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1624f-121">See also</span></span>

- [<span data-ttu-id="1624f-122">\<supportPortability> Element</span><span class="sxs-lookup"><span data-stu-id="1624f-122">\<supportPortability> Element</span></span>](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)
- [<span data-ttu-id="1624f-123">Options du compilateur C# par ordre alphabétique</span><span class="sxs-lookup"><span data-stu-id="1624f-123">C# Compiler Options Listed Alphabetically</span></span>](./listed-alphabetically.md)
