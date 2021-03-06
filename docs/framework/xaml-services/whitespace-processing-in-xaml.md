---
title: Traitement des espaces blancs en XAML
ms.date: 03/30/2017
helpviewer_keywords:
- East Asian characters [XAML Services]
- XAML [XAML Services], white-space processing
- white-space processing in XAML [XAML Services]
- characters [XAML Services], East Asian
ms.assetid: cc9cc377-7544-4fd0-b65b-117b90bb0b23
ms.openlocfilehash: 077f19690d204d3b8f682d01c51feee9e9edbfd4
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796813"
---
# <a name="white-space-processing-in-xaml"></a>Traitement des espaces blancs en XAML
Les règles de langage pour l’État XAML dont l’espace blanc significatif doit être [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] traité par une implémentation du processeur. Cette rubrique documente ces règles de langage XAML. Il documente également la gestion des espaces blancs supplémentaires définie par [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] l’implémentation du processeur XAML et du writer XAML pour la sérialisation.  
  
<a name="whitespace_definition"></a>   
## <a name="white-space-definition"></a>Définition de l’espace blanc  
 Cohérent avec [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)], les espaces blancs dans sont [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] l’espace, le saut de ligne et la tabulation. Ils correspondent respectivement aux valeurs [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] 0020, 000A et 0009, respectivement.  
  
<a name="whitespace_normalization"></a>   
## <a name="white-space-normalization"></a>Normalisation des espaces blancs  
 Par défaut, la normalisation d’espace blanc suivante se produit lorsqu' [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] un processeur traite [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] un fichier:  
  
1. Les caractères de saut de ligne entre les caractères d'Extrême-Orient sont supprimés. Consultez la section « Caractères d'Extrême-Orient », plus loin dans cette rubrique, pour obtenir une définition de ce terme.  
  
2. Tous les caractères d’espace blanc (espace, saut de ligne, tabulation) sont convertis en espaces.  
  
3. Tous les espaces consécutifs sont supprimés et remplacés par un espace.  
  
4. Un espace qui suit immédiatement la balise de début est supprimé.  
  
5. Un espace qui précède immédiatement la balise de fin est supprimé.  
  
 La « valeur par défaut » correspond à l'état désigné par la valeur par défaut de l'attribut [xml:space](xml-space-handling-in-xaml.md) .  
  
<a name="whitespace_in_inner_text_and_string_primitives"></a>   
## <a name="white-space-in-inner-text-and-string-primitives"></a>Espace blanc dans le texte interne et primitives de chaîne  
 Les règles de normalisation précédentes s'appliquent au texte interne que l'on trouve dans les éléments XAML. Après la normalisation, un processeur XAML convertit tout texte interne en un type approprié, comme suit :  
  
- Si le type de la propriété n'est pas une collection, mais n'est pas directement un type <xref:System.Object> , le processeur XAML tente de convertir en ce type à l'aide de son convertisseur de type. En cas d'échec de la conversion, une erreur de compilation survient.  
  
- Si le type de la propriété est une collection et que le texte interne est contigu (aucune balise d'élément intermédiaire), le texte interne est analysé comme un élément <xref:System.String>String. Si le type de collection ne peut pas accepter <xref:System.String>, une erreur de compilation est également générée.  
  
- Si le type de la propriété est <xref:System.Object>, le texte interne est analysé comme un objet <xref:System.String>unique. En cas de balises d'élément intermédiaires, une erreur de compilation est générée car le type <xref:System.Object> implique un objet unique (<xref:System.String> ou autre).  
  
- Si le type de la propriété est une collection et que le texte interne n'est pas contigu, la première sous-chaîne est convertie en <xref:System.String> et ajoutée en tant qu'élément de collection, l'élément intermédiaire est ajouté en tant qu'élément de collection et la sous-chaîne de fin (le cas échéant) est ajoutée à la collection comme troisième élément <xref:System.String> .  
  
<a name="preserving_whitespace"></a>   
## <a name="preserving-white-space"></a>Conservation des espaces blancs  
 Il existe plusieurs techniques permettant de conserver l’espace blanc dans [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] la source pour une présentation finale qui n' [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] est pas affectée par la normalisation des espaces blancs du processeur.  
  
 **XML: Space = "preserve"** : Spécifiez cet attribut au niveau de l’élément où la conservation de l’espace blanc est souhaitée. Cela permet de conserver l'ensemble de l'espace blanc, ce qui inclut les espaces pouvant être ajoutés par des applications d'édition de code pour imprimer correctement des éléments comme une imbrication visuellement intuitive. Toutefois, le rendu de ces espaces est déterminé par le modèle de contenu pour l'élément conteneur. Évitez de `xml:space="preserve"` spécifier au niveau racine, car la plupart des modèles objet ne considèrent pas les espaces blancs comme significatifs, quelle que soit la façon dont vous définissez l’attribut. Le fait de définir `xml:space` de façon globale peut avoir des conséquences sur les performances de traitement XAML (en particulier, la sérialisation) dans certaines implémentations. Il est recommandé de définir uniquement l’attribut spécifiquement au niveau des éléments qui restituent l’espace blanc dans les chaînes ou qui sont des collections significatives d’espaces blancs.  
  
 **Entités et espaces insécables**: le langage [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] prend en charge l'insertion d'une entité [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] dans un modèle objet de texte. Vous pouvez utiliser des entités dédiées telles que l’espace insécable (\#& 160; dans l’encodage UTF-8). Vous pouvez également utiliser des contrôles de texte enrichi qui prennent en charge les caractères d'espace insécable. Soyez prudent lorsque vous utilisez des entités pour simuler des caractéristiques de mise en page telles que la mise en retrait, car la sortie à l'exécution des entités variera suivant que le nombre de facteurs est plus élevé que les fonctionnalités de mise en page générales, telles que l'utilisation appropriée de panneaux et de marges. Par exemple, les entités sont mappées aux polices et peuvent changer de taille en fonction de la police sélectionnée par l'utilisateur.  
  
<a name="east_asian_characters"></a>   
## <a name="east-asian-characters"></a>Caractères d’Extrême-Orient  
 Les caractères d'Extrême-Orient sont définis comme un jeu de caractères [!INCLUDE[TLA2#tla_unicode](../../../includes/tla2sharptla-unicode-md.md)] allant de U+20000 à U+2FFFD et de U+30000 à U+3FFFD. Ce sous-ensemble est parfois également appelé « idéogrammes CJK ». Pour plus d'informations, consultez <https://www.unicode.org>.  
  
<a name="whitespace_and_text_content_models"></a>   
## <a name="white-space-and-text-content-models"></a>Modèles d’espace blanc et de contenu de texte  
 En pratique, la conservation de l’espace blanc ne pose problème que pour un sous-ensemble de tous les modèles de contenu possibles. Ce sous-ensemble se compose des modèles de contenu qui peuvent prendre un type <xref:System.String> singleton d'une certaine manière, une collection <xref:System.String> dédiée ou un mélange de <xref:System.String> et d'autres types dans une collection <xref:System.Collections.IList> ou <xref:System.Collections.Generic.ICollection%601> .  
  
### <a name="white-space-and-text-content-models-in-wpf"></a>Modèles d’espace blanc et de contenu de texte dans WPF  
 À des fins d'illustration, le reste de cette section référence des types particuliers définis par WPF. Les fonctionnalités de gestion de l’espace blanc décrites dans cette rubrique sont généralement pertinentes pour les .NET Framework les services XAML et WPF. Pour voir ce comportement en action, il peut se révéler utile d'expérimenter des balises XAML WPF et de consulter les résultats dans un graphique d'objets, puis de procéder une nouvelle fois à une désérialisation en balises.  
  
 Même pour les modèles de contenu qui peuvent prendre des chaînes, le comportement par défaut au sein de ces modèles de contenu est que tout espace blanc restant n’est pas traité comme significatif. Par exemple, <xref:System.Windows.Controls.ListBox> prend un <xref:System.Collections.IList>, mais l’espace blanc (par exemple, les sauts de ligne entre chaque <xref:System.Windows.Controls.ListBoxItem>) n’est pas conservé et n’est pas rendu. Si vous tentez d'utiliser des sauts de ligne comme séparateurs entre des chaînes pour les éléments <xref:System.Windows.Controls.ListBoxItem> , cela ne fonctionne pas du tout ; les chaînes séparées par des sauts de ligne sont traitées comme une chaîne et un élément.  
  
 Les collections qui traitent les espaces blancs comme significatifs font généralement partie du modèle de document dynamique. La collection principale qui prend en charge le comportement de conservation <xref:System.Windows.Documents.InlineCollection>de l’espace blanc est. Cette classe de collection est déclarée <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>avec. Lorsque cet attribut est trouvé, [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] le processeur traite l’espace blanc dans la collection comme significatif. La combinaison de `xml:space="preserve"` et de l’espace blanc <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> dans une collection dénotée est que tous les espaces blancs sont conservés et rendus. La combinaison de `xml:space="default"` et de l’espace blanc <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> dans un entraîne la normalisation initiale de l’espace blanc décrite plus haut, ce qui laisse un espace à certaines positions, et ces espaces sont conservés et rendus. À vous de déterminer le comportement souhaité et d'utiliser `xml:space` de manière sélective pour activer le comportement de votre choix.  
  
 En outre, certains éléments inline qui indiquent un LineBreak dans un modèle de document dynamique ne doivent pas introduire délibérément un espace supplémentaire, même dans une collection significative d’espaces blancs. Par exemple, l' <xref:System.Windows.Documents.LineBreak> élément a le même objectif que la \<balise br/> en HTML, et pour une meilleure lisibilité dans le <xref:System.Windows.Documents.LineBreak> balisage, en général, un est séparé du texte suivant par un saut de page créé. Ce saut de ligne ne doit pas être normalisé pour devenir un espace de début dans la ligne suivante. Pour activer ce comportement, la définition de classe pour <xref:System.Windows.Documents.LineBreak> l’élément applique <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>le, qui est ensuite interprété par [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] le processeur pour signifier que l’espace <xref:System.Windows.Documents.LineBreak> blanc autour est toujours rogné.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du langage XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md)
- [Entités de caractères XML et XAML](xml-character-entities-and-xaml.md)
- [gestion XML: Space en XAML](xml-space-handling-in-xaml.md)
