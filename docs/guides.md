---
layout: docwithnav
title: Guides
notitle: 'true'
---

# guides

  
  
    var reportedSearchInputs = \[\];  
    var searchPageCount = 0;  
  
    document.onmousemove = function\(e\) {  
        var event = e \|\| window.event;  
        window.mouseX = event.clientX;  
        window.mouseY = event.clientY;  
        if \(checkMouseMoved\(\)\) {  
            checkSearchInput\(\);  
        }  
    };  
  
    jqueryDefer\(function \(\) {  
        var searchInput = $\('\#searchGuideInput'\);  
        searchInput.keyup\(function\(\) {  
            window.typeMouseX = window.mouseX;  
            window.typeMouseY = window.mouseY;  
            filterGuides\(\);  
        }\);  
        searchInput.blur\(function\(\) {  
            checkSearchInput\(\);  
        }\);  
        filterGuides\(\);  
    }\);  
  
    function checkMouseMoved \(\) {  
        if \(typeof window.typeMouseX === "undefined" \|\| typeof window.typeMouseY === "undefined"\) {  
            return false;  
        }  
        return window.typeMouseX !== window.mouseX && window.typeMouseY !== window.mouseY;  
    }  
  
    function filterGuides\(\) {  
        $\('.guides-list'\).find\('.guide-container'\).removeClass\('hidden'\);  
        var guidesBlock = $\('.guides-block'\);  
        guidesBlock.removeClass\('hidden'\);  
        searchPageCount = 0;  
        var searchText = $\('\#searchGuideInput'\).val\(\);  
  
        var keywords = searchText.split\(' '\);  
        if \(keywords && keywords.length\) {  
            var keyRegexps = \[\];  
            for \(var i=0;i&lt;keywords.length;i++\) {  
                if \(keywords\[i\].length\) {  
                    keyRegexps.push\(new RegExp\(keywords\[i\].toLowerCase\(\)\)\);  
                }  
            }  
            guidesBlock.each\( function\(\) {  
                var containers = $\( this \).find\('.guide-container'\);  
                var total = containers.length;  
                containers.each\( function\(\) {  
                    var paragraphs = $\(this\).find\('p'\);  
                    var text = '';  
                    paragraphs.each\( function\(\) {  
                        text += $\(this\).html\(\);  
                        text += ' ';  
                    }\);  
                    var matches = testKeywords\(keyRegexps, text.toLowerCase\(\)\);  
                    if \(!matches\) {  
                        $\( this \).addClass\('hidden'\);  
                        total--;  
                    }  
                }\);  
                searchPageCount += total;  
                if \(!total\) {  
                    $\( this \).addClass\('hidden'\);  
                }  
            }\);  
        }  
    }  
  
    function testKeywords\(keyRegexps, input\) {  
        var result = true;  
        for \(var i=0;i&lt;keyRegexps.length;i++\) {  
            result = result && keyRegexps\[i\].test\(input\);  
        }  
        return result;  
    }  
  
    function checkSearchInput\(\) {  
        var searchText = $\('\#searchGuideInput'\).val\(\).trim\(\);  
        if \(searchText.length &gt;=3 && reportedSearchInputs.indexOf\(searchText\) === -1\) {  
            reportSearchInput\(searchText\);  
            reportedSearchInputs.push\(searchText\);  
        }  
    }  
  
    function reportSearchInput\(searchText\) {  
  
        if \(!ga.hasOwnProperty\("loaded"\) \|\| ga.loaded !== true\) {  
            return;  
        }  
  
        ga\(  
            "send", "event", "Guides", "search",  
            searchText, searchPageCount  
        \);  
    }  
  


  {% assign guides = site.data.guides-data %}{% include guides.html %}

