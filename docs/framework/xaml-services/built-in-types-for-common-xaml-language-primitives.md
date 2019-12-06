---
title: Types intégrés pour les primitives associées au langage XAML courant
ms.date: 03/30/2017
helpviewer_keywords:
- XAML language primitives [XAML Services]
- XAML [XAML Services], built-in types
- x:String [XAML Services]
- x:TimeSpan [XAML Services]
- x:Byte [XAML Services]
- x:Double [XAML Services]
- XAML [XAML Services], types
- x:Uri [XAML Services]
- XAML built-in types [XAML Services]
- x:Int64 [XAML Services]
- x:Single [XAML Services]
- x:Int32 [XAML Services]
ms.assetid: 11de2f08-5b95-4989-b5ec-5178eb968184
ms.openlocfilehash: c6af46fe2ea21d081e693ee83949651bd388a045
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837270"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a><span data-ttu-id="7c882-102">Types intégrés pour les primitives associées au langage XAML courant</span><span class="sxs-lookup"><span data-stu-id="7c882-102">Built-in Types for Common XAML Language Primitives</span></span>
<span data-ttu-id="7c882-103">XAML 2009 introduit la prise en charge de niveau de langage XAML pour plusieurs types de données qui sont des primitives fréquemment utilisées dans le Common Language Runtime (CLR) et dans d'autres langages de programmation.</span><span class="sxs-lookup"><span data-stu-id="7c882-103">XAML 2009 introduces XAML language-level support for several data types that are frequently used primitives in the common language runtime (CLR) and in other programming languages.</span></span> <span data-ttu-id="7c882-104">XAML 2009 ajoute la prise en charge des primitives suivantes : `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`et `x:Array`</span><span class="sxs-lookup"><span data-stu-id="7c882-104">XAML 2009 adds support for these primitives: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, and `x:Array`</span></span>  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a><span data-ttu-id="7c882-105">Techniques précédentes pour les primitives du langage dans le balisage XAML</span><span class="sxs-lookup"><span data-stu-id="7c882-105">Previous Techniques for Language Primitives in XAML Markup</span></span>  
 <span data-ttu-id="7c882-106">En XAML, pour les versions précédentes de WPF, vous pouviez faire référence aux primitives du langage CLR en mappant l'assembly et l'espace de noms qui contenaient une classe de définition de primitive CLR pour le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7c882-106">In XAML for previous WPF versions, you could reference the CLR language primitives by mapping the assembly and namespace that contained a CLR primitive definition class for the .NET Framework.</span></span> <span data-ttu-id="7c882-107">La plupart d'entre elles se trouvent dans l'assembly mscorlib et dans l'espace de noms <xref:System> .</span><span class="sxs-lookup"><span data-stu-id="7c882-107">Most of these are in the mscorlib assembly and <xref:System> namespace.</span></span> <span data-ttu-id="7c882-108">Par exemple, pour utiliser <xref:System.Int32>, vous pouviez déclarer le mappage suivant (avec un exemple d'utilisation indiqué ensuite) :</span><span class="sxs-lookup"><span data-stu-id="7c882-108">For example, to use <xref:System.Int32>, you could declare the following mapping (with an example usage shown thereafter):</span></span>  
  
```xaml  
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"   
xmlns:sys="clr-namespace:System;assembly=mscorlib">  
  <Application.Resources>  
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>  
  </Application.Resources>  
</Application>  
```  
  
<a name="xaml_2009_language_primitives"></a>   
## <a name="xaml-2009-language-primitives"></a><span data-ttu-id="7c882-109">Primitives de langage XAML 2009</span><span class="sxs-lookup"><span data-stu-id="7c882-109">XAML 2009 Language Primitives</span></span>  
 <span data-ttu-id="7c882-110">Par convention, les primitives de langage pour XAML et tous les autres éléments de langage XAML sont affichés, notamment le préfixe `x:` .</span><span class="sxs-lookup"><span data-stu-id="7c882-110">By convention, the language primitives for XAML and all other XAML language elements are shown, including the `x:` prefix.</span></span> <span data-ttu-id="7c882-111">C'est ainsi que les éléments de langage XAML sont généralement utilisés dans le balisage réel.</span><span class="sxs-lookup"><span data-stu-id="7c882-111">This is how XAML language elements are typically used in real-world markup.</span></span> <span data-ttu-id="7c882-112">Cette convention est suivie de la documentation conceptuelle pour XAML dans WPF, ainsi que dans la spécification XAML.</span><span class="sxs-lookup"><span data-stu-id="7c882-112">This convention is followed in the conceptual documentation for XAML in WPF and also in the XAML specification.</span></span>  
  
### <a name="xobject"></a><span data-ttu-id="7c882-113">x:Object</span><span class="sxs-lookup"><span data-stu-id="7c882-113">x:Object</span></span>  
 <span data-ttu-id="7c882-114">Pour le stockage CLR, la primitive `x:Object` correspond à <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="7c882-114">For CLR backing, the `x:Object` primitive corresponds to <xref:System.Object>.</span></span>  
  
 <span data-ttu-id="7c882-115">Cette primitive n'est généralement pas utilisée dans le balisage d'application, mais elle peut être utile pour certains scénarios tels que la vérification de l'assignabilité dans un système de type XAML.</span><span class="sxs-lookup"><span data-stu-id="7c882-115">This primitive is not typically used in application markup, but might be useful for some scenarios such as checking assignability in a XAML type system.</span></span>  
  
### <a name="xboolean"></a><span data-ttu-id="7c882-116">x:Boolean</span><span class="sxs-lookup"><span data-stu-id="7c882-116">x:Boolean</span></span>  
 <span data-ttu-id="7c882-117">Pour le stockage CLR, la primitive `x:Boolean` correspond à <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="7c882-117">For CLR backing, the `x:Boolean` primitive corresponds to <xref:System.Boolean>.</span></span>  
  
 <span data-ttu-id="7c882-118">XAML analyse les valeurs de `x:Boolean` sans respect de la casse.</span><span class="sxs-lookup"><span data-stu-id="7c882-118">XAML parses values for `x:Boolean` as case insensitive.</span></span> <span data-ttu-id="7c882-119">Notez que `x:Bool` n'est pas une alternative acceptée.</span><span class="sxs-lookup"><span data-stu-id="7c882-119">Note that `x:Bool` is not an accepted alternative.</span></span> <span data-ttu-id="7c882-120">Pour obtenir la définition de la spécification du langage XAML, consultez [\[sections MS-xaml\] 5.2.17 et 5.4.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7c882-120">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.17 and 5.4.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xchar"></a><span data-ttu-id="7c882-121">x:Char</span><span class="sxs-lookup"><span data-stu-id="7c882-121">x:Char</span></span>  
 <span data-ttu-id="7c882-122">Pour le stockage CLR, la primitive `x:Char` correspond à <xref:System.Char>.</span><span class="sxs-lookup"><span data-stu-id="7c882-122">For CLR backing, the `x:Char` primitive corresponds to <xref:System.Char>.</span></span>  
  
 <span data-ttu-id="7c882-123">Les types de chaîne et de caractère ont une interaction avec l'encodage global du fichier au niveau XML.</span><span class="sxs-lookup"><span data-stu-id="7c882-123">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="7c882-124">Pour obtenir la définition de la spécification du langage XAML, consultez [\[sections MS-xaml\] 5.2.7 et 5.4.1](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7c882-124">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.7 and 5.4.1](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xstring"></a><span data-ttu-id="7c882-125">x:String</span><span class="sxs-lookup"><span data-stu-id="7c882-125">x:String</span></span>  
 <span data-ttu-id="7c882-126">Pour le stockage CLR, la primitive `x:String` correspond à <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="7c882-126">For CLR backing, the `x:String` primitive corresponds to <xref:System.String>.</span></span>  
  
 <span data-ttu-id="7c882-127">Les types de chaîne et de caractère ont une interaction avec l'encodage global du fichier au niveau XML.</span><span class="sxs-lookup"><span data-stu-id="7c882-127">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="7c882-128">Pour obtenir la définition de la spécification du langage XAML, consultez [\[MS-xaml\] sections 5.2.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7c882-128">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xdecimal"></a><span data-ttu-id="7c882-129">x:Decimal</span><span class="sxs-lookup"><span data-stu-id="7c882-129">x:Decimal</span></span>  
 <span data-ttu-id="7c882-130">Pour le stockage CLR, la primitive `x:Decimal` correspond à <xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="7c882-130">For CLR backing, the `x:Decimal` primitive corresponds to <xref:System.Decimal>.</span></span>  
  
 <span data-ttu-id="7c882-131">Notez que l'analyse XAML est effectuée fondamentalement par rapport à la culture `en-US` .</span><span class="sxs-lookup"><span data-stu-id="7c882-131">Note that XAML parsing is inherently done under `en-US` culture.</span></span> <span data-ttu-id="7c882-132">Dans la culture `en-US` , le séparateur approprié pour les composants d'une valeur décimale est toujours le point (`.`), indépendamment des paramètres de culture de l'environnement de développement, ou de la cible cliente éventuelle où le code XAML est chargé au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="7c882-132">Under `en-US` culture, the correct separator for the components of a decimal is always a period (`.`) regardless of culture settings of the development environment, or of the eventual client target where the XAML is loaded at run time.</span></span>  
  
 <span data-ttu-id="7c882-133">Pour obtenir la définition de la spécification du langage XAML, consultez [\[sections MS-xaml\] 5.2.14 et 5.4.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7c882-133">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.14 and 5.4.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xsingle"></a><span data-ttu-id="7c882-134">x:Single</span><span class="sxs-lookup"><span data-stu-id="7c882-134">x:Single</span></span>  
 <span data-ttu-id="7c882-135">Pour le stockage CLR, la primitive `x:Single` correspond à <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="7c882-135">For CLR backing, the `x:Single` primitive corresponds to <xref:System.Single>.</span></span>  
  
 <span data-ttu-id="7c882-136">Outre les valeurs numériques, la syntaxe de texte de `x:Single` autorise également les jetons `Infinity`, `-Infinity`et `NaN`.</span><span class="sxs-lookup"><span data-stu-id="7c882-136">In addition to the numeric values, text syntax for `x:Single` also permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="7c882-137">Ces jetons sont traités avec respect de la casse.</span><span class="sxs-lookup"><span data-stu-id="7c882-137">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="7c882-138">`x:Single` peut prendre en charge les valeurs sous forme de notation scientifique, si le premier caractère dans la syntaxe de texte est `e` ou `E`.</span><span class="sxs-lookup"><span data-stu-id="7c882-138">`x:Single` can support values in scientific notation form, if the first character in text syntax is `e` or `E`.</span></span>  
  
 <span data-ttu-id="7c882-139">Pour obtenir la définition de la spécification du langage XAML, consultez [\[sections MS-xaml\] 5.2.8 et 5.4.2](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7c882-139">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.8 and 5.4.2](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xdouble"></a><span data-ttu-id="7c882-140">x:Double</span><span class="sxs-lookup"><span data-stu-id="7c882-140">x:Double</span></span>  
 <span data-ttu-id="7c882-141">Pour le stockage CLR, la primitive `x:Double` correspond à <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="7c882-141">For CLR backing, the `x:Double` primitive corresponds to <xref:System.Double>.</span></span>  
  
 <span data-ttu-id="7c882-142">Outre les valeurs numériques, la syntaxe de texte de `x:Double` autorise les jetons `Infinity`, `-Infinity`et `NaN`.</span><span class="sxs-lookup"><span data-stu-id="7c882-142">In addition to the numeric values, text syntax for `x:Double` permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="7c882-143">Ces jetons sont traités avec respect de la casse.</span><span class="sxs-lookup"><span data-stu-id="7c882-143">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="7c882-144">`x:Double` peut prendre en charge les valeurs sous forme de notation scientifique.</span><span class="sxs-lookup"><span data-stu-id="7c882-144">`x:Double` can support values in scientific notation form.</span></span> <span data-ttu-id="7c882-145">Utilisez le caractère `e` ou `E` pour introduire la partie exposant.</span><span class="sxs-lookup"><span data-stu-id="7c882-145">Use the character `e` or `E` to introduce the exponent portion.</span></span>  
  
 <span data-ttu-id="7c882-146">Pour obtenir la définition de la spécification du langage XAML, consultez [\[sections MS-xaml\] 5.2.9 et 5.4.3](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7c882-146">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.9 and 5.4.3](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xint16"></a><span data-ttu-id="7c882-147">x:Int16</span><span class="sxs-lookup"><span data-stu-id="7c882-147">x:Int16</span></span>  
 <span data-ttu-id="7c882-148">Pour le stockage CLR, la primitive `x:Int16` correspond à <xref:System.Int16> et `x:Int16` est considérée comme signée.</span><span class="sxs-lookup"><span data-stu-id="7c882-148">For CLR backing, the `x:Int16` primitive corresponds to <xref:System.Int16> and `x:Int16` is treated as signed.</span></span> <span data-ttu-id="7c882-149">En XAML, l'absence d'un signe plus (`+`) dans la syntaxe de texte indique implicitement une valeur signée positive.</span><span class="sxs-lookup"><span data-stu-id="7c882-149">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="7c882-150">Pour obtenir la définition de la spécification du langage XAML, consultez [\[sections MS-xaml\] 5.2.11 et 5.4.5](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7c882-150">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.11 and 5.4.5](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xint32"></a><span data-ttu-id="7c882-151">x:Int32</span><span class="sxs-lookup"><span data-stu-id="7c882-151">x:Int32</span></span>  
 <span data-ttu-id="7c882-152">Pour le stockage CLR, la primitive `x:Int32` correspond à <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="7c882-152">For CLR backing, the `x:Int32` primitive corresponds to <xref:System.Int32>.</span></span> <span data-ttu-id="7c882-153">`x:Int32` est considérée comme signée.</span><span class="sxs-lookup"><span data-stu-id="7c882-153">`x:Int32` is treated as signed.</span></span> <span data-ttu-id="7c882-154">En XAML, l'absence d'un signe plus (`+`) dans la syntaxe de texte indique implicitement une valeur signée positive.</span><span class="sxs-lookup"><span data-stu-id="7c882-154">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="7c882-155">Pour obtenir la définition de la spécification du langage XAML, consultez [\[sections MS-xaml\] 5.2.12 et 5.4.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7c882-155">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.12 and 5.4.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xint64"></a><span data-ttu-id="7c882-156">x:Int64</span><span class="sxs-lookup"><span data-stu-id="7c882-156">x:Int64</span></span>  
 <span data-ttu-id="7c882-157">Pour le stockage CLR, la primitive `x:Int64` correspond à <xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="7c882-157">For CLR backing, the `x:Int64` primitive corresponds to <xref:System.Int64>.</span></span> <span data-ttu-id="7c882-158">`x:Int64` est considérée comme signée.</span><span class="sxs-lookup"><span data-stu-id="7c882-158">`x:Int64` is treated as signed.</span></span> <span data-ttu-id="7c882-159">En XAML, l'absence d'un signe plus (`+`) dans la syntaxe de texte indique implicitement une valeur signée positive.</span><span class="sxs-lookup"><span data-stu-id="7c882-159">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="7c882-160">Pour obtenir la définition de la spécification du langage XAML, consultez [\[sections MS-xaml\] 5.2.13 et 5.4.7](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7c882-160">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.13 and 5.4.7](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xtimespan"></a><span data-ttu-id="7c882-161">x:TimeSpan</span><span class="sxs-lookup"><span data-stu-id="7c882-161">x:TimeSpan</span></span>  
 <span data-ttu-id="7c882-162">Pour le stockage CLR, la primitive `x:TimeSpan` correspond à <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="7c882-162">For CLR backing, the `x:TimeSpan` primitive corresponds to <xref:System.TimeSpan>.</span></span>  
  
 <span data-ttu-id="7c882-163">Notez que l'analyse XAML pour le format heure-date est effectuée fondamentalement par rapport à la culture `en-US` .</span><span class="sxs-lookup"><span data-stu-id="7c882-163">Note that XAML parsing for time-date format is inherently done under `en-US` culture.</span></span>  
  
 <span data-ttu-id="7c882-164">Pour obtenir la définition de la spécification du langage XAML, consultez [\[sections MS-xaml\] 5.2.16 et 5.4.10](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7c882-164">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.16 and 5.4.10](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xuri"></a><span data-ttu-id="7c882-165">x:Uri</span><span class="sxs-lookup"><span data-stu-id="7c882-165">x:Uri</span></span>  
 <span data-ttu-id="7c882-166">Pour le stockage CLR, la primitive `x:Uri` correspond à <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="7c882-166">For CLR backing, the `x:Uri` primitive corresponds to <xref:System.Uri>.</span></span>  
  
 <span data-ttu-id="7c882-167">La vérification des protocoles ne fait pas partie de la définition XAML de `x:Uri`.</span><span class="sxs-lookup"><span data-stu-id="7c882-167">Checking for protocols is not part of the XAML definition for `x:Uri`.</span></span>  
  
 <span data-ttu-id="7c882-168">Pour obtenir la définition de la spécification du langage XAML, consultez [\[sections MS-xaml\] 5.2.15 et 5.4.9](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7c882-168">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.15 and 5.4.9](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xbyte"></a><span data-ttu-id="7c882-169">x:Byte</span><span class="sxs-lookup"><span data-stu-id="7c882-169">x:Byte</span></span>  
 <span data-ttu-id="7c882-170">Pour le stockage CLR, la primitive `x:Byte` correspond à <xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="7c882-170">For CLR backing, the `x:Byte` primitive corresponds to <xref:System.Byte>.</span></span> <span data-ttu-id="7c882-171">Une <xref:System.Byte> / `x:Byte` est traitée comme non signée.</span><span class="sxs-lookup"><span data-stu-id="7c882-171">A <xref:System.Byte> / `x:Byte` is treated as unsigned.</span></span>  
  
 <span data-ttu-id="7c882-172">Pour obtenir la définition de la spécification du langage XAML, consultez [\[sections MS-xaml\] 5.2.10 et 5.4.4](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7c882-172">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.10 and 5.4.4](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
### <a name="xarray"></a><span data-ttu-id="7c882-173">x:Array</span><span class="sxs-lookup"><span data-stu-id="7c882-173">x:Array</span></span>  
 <span data-ttu-id="7c882-174">Pour le stockage CLR, la primitive `x:Array` correspond à <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="7c882-174">For CLR backing, the `x:Array` primitive corresponds to <xref:System.Array>.</span></span>  
  
 <span data-ttu-id="7c882-175">Vous pouvez définir un tableau dans XAML 2006 à l'aide d'une syntaxe d'extension de balisage ; toutefois, la syntaxe XAML 2009 est une primitive définie par le langage qui ne requiert pas l'accès à une extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="7c882-175">You can define an array in XAML 2006  by using a markup extension syntax; however, the XAML 2009 syntax is a language-defined primitive that does not require accessing a markup extension.</span></span> <span data-ttu-id="7c882-176">Pour plus d’informations sur la prise en charge de XAML 2006, consultez [x:Array Markup Extension](x-array-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="7c882-176">For more information about XAML 2006 support, see [x:Array Markup Extension](x-array-markup-extension.md).</span></span>  
  
 <span data-ttu-id="7c882-177">Pour obtenir la définition de la spécification du langage XAML, consultez [\[sections MS-xaml\] 5.2.18](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7c882-177">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.18](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a><span data-ttu-id="7c882-178">Prise en charge de WPF</span><span class="sxs-lookup"><span data-stu-id="7c882-178">WPF Support</span></span>  
 <span data-ttu-id="7c882-179">Dans WPF, vous pouvez utiliser les fonctionnalités XAML 2009, mais uniquement pour le code XAML qui n'est pas compilé par balisage.</span><span class="sxs-lookup"><span data-stu-id="7c882-179">In WPF, you can use XAML 2009 features but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="7c882-180">Le code XAML compilé par balisage pour WPF et la forme BAML du code XAML ne prennent actuellement pas en charge les mots clés et les fonctionnalités XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="7c882-180">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
 <span data-ttu-id="7c882-181">La création de code XAML libre, suivie du chargement de ce code XAML dans une exécution de WPF et dans un graphique d'objets avec <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>constitue un scénario dans lequel vous pouvez utiliser les fonctionnalités XAML 2009 avec WPF.</span><span class="sxs-lookup"><span data-stu-id="7c882-181">A scenario where you can use XAML 2009 features together with WPF is if you author loose XAML and you then load that XAML into a WPF runtime and object graph with <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7c882-182">La classe <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> WPF et sa méthode <xref:System.Windows.Markup.XamlReader.Load%2A> peuvent traiter les mots clés de langage et fonctionnalités XAML 2009 dans une représentation de graphique d'objets valide.</span><span class="sxs-lookup"><span data-stu-id="7c882-182">The WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> and its <xref:System.Windows.Markup.XamlReader.Load%2A> can process XAML 2009 language keywords and features into a valid object graph representation.</span></span>
