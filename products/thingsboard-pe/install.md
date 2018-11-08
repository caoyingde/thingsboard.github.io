---
layout: docwithnav
title: Get ThingsBoard Professional Edition
description: ThingsBoard Professional Edition Installation
hidetoc: 'true'
---

# install

  
    jqueryDefer\(function \(\) {  
            var trialMarketplace = $\('\#trial-marketplace'\);  
            var peCloudTrial = $\('\#pe-cloud-trial'\);  
            var awsTrial = $\('\#aws-trial-market'\);  
            var azureTrial = $\('\#azure-trial-market'\);  
  
            var awsTrialForm = $\('\#mlb2-7972110'\);              
            var azureTrialForm = $\('\#mlb2-9674300'\);  
  
            peCloudTrial.click\(function\(\) {  
                window.open\('https://cloud.thingsboard.io/signup', '\_blank'\);  
            }\);  
  
            awsTrial.click\(function\(\) {  
                trialMarketplace.css\('display', 'none'\);  
                awsTrialForm.css\('display', ''\);  
            }\);  
            azureTrial.click\(function\(\) {  
                trialMarketplace.css\('display', 'none'\);  
                azureTrialForm.css\('display', ''\);  
            }\);  
  
            var payGoMarketplace = $\('\#pay-go-marketplace'\);  
            var awsPayGo = $\('\#aws-pay-go-market'\);  
            var azurePayGo = $\('\#azure-pay-go-market'\);  
  
            var awsPayGoForm = $\('\#mlb2-7520964'\);              
            var azurePayGoForm = $\('\#mlb2-9674436'\);  
  
            awsPayGo.click\(function\(\) {  
                payGoMarketplace.css\('display', 'none'\);  
                awsPayGoForm.css\('display', ''\);  
            }\);  
            azurePayGo.click\(function\(\) {  
                payGoMarketplace.css\('display', 'none'\);  
                azurePayGoForm.css\('display', ''\);  
            }\);  
  
        }\);  


  Free trial

  
     function ml\_webform\_success\_7972110\(\) {  
        var $ = ml\_jQuery \|\| jQuery;          
        $\(location\).attr\('href', '/products/thingsboard-pe/install-thanks/?deploy=trial'\);  
        //$\('.ml-subscribe-form-7972110 .ml-block-success'\).show\(\);  
        //$\('.ml-subscribe-form-7972110 .ml-block-form'\).hide\(\);  
        //$\('html, body'\).animate\({  
        //    scrollTop: $\('\#tab-cloud'\).offset\(\).top - 100  
        //  }, 0\);  
        //$\('.ml-subscribe-form-7520964 .ml-block-success'\).addClass\("animated zoomIn"\);  
    };  
     function ml\_webform\_success\_9674300\(\) {  
        var $ = ml\_jQuery \|\| jQuery;          
        $\(location\).attr\('href', '/products/thingsboard-pe/install-thanks/?deploy=trial'\);  
        //$\('.ml-subscribe-form-9674300 .ml-block-success'\).show\(\);  
        //$\('.ml-subscribe-form-9674300 .ml-block-form'\).hide\(\);  
        //$\('html, body'\).animate\({  
        //    scrollTop: $\('\#tab-cloud'\).offset\(\).top - 100  
        //  }, 0\);  
        //$\('.ml-subscribe-form-9674300 .ml-block-success'\).addClass\("animated zoomIn"\);  
    };  
    function ml\_webform\_success\_7520964\(\) {  
        var $ = ml\_jQuery \|\| jQuery;          
        $\(location\).attr\('href', '/products/thingsboard-pe/install-thanks/?deploy=cloud'\);  
        //$\('.ml-subscribe-form-7520964 .ml-block-success'\).show\(\);  
        //$\('.ml-subscribe-form-7520964 .ml-block-form'\).hide\(\);  
        //$\('html, body'\).animate\({  
        //    scrollTop: $\('\#tab-cloud'\).offset\(\).top - 100  
        //  }, 0\);  
        //$\('.ml-subscribe-form-7520964 .ml-block-success'\).addClass\("animated zoomIn"\);  
    };  
    function ml\_webform\_success\_9674436\(\) {  
        var $ = ml\_jQuery \|\| jQuery;          
        $\(location\).attr\('href', '/products/thingsboard-pe/install-thanks/?deploy=cloud'\);  
        //$\('.ml-subscribe-form-9674436 .ml-block-success'\).show\(\);  
        //$\('.ml-subscribe-form-9674436 .ml-block-form'\).hide\(\);  
        //$\('html, body'\).animate\({  
        //    scrollTop: $\('\#tab-cloud'\).offset\(\).top - 100  
        //  }, 0\);  
        //$\('.ml-subscribe-form-9674436 .ml-block-success'\).addClass\("animated zoomIn"\);  
    };      
    function ml\_webform\_success\_7556612\(\) {  
        var $ = ml\_jQuery \|\| jQuery;         
        $\(location\).attr\('href', '/products/thingsboard-pe/install-thanks/?deploy=premise'\);  
        //$\('.ml-subscribe-form-7556612 .ml-block-success'\).show\(\);  
        //$\('.ml-subscribe-form-7556612 .ml-block-form'\).hide\(\);  
        //$\('html, body'\).animate\({  
        //    scrollTop: $\('\#tab-on-premise'\).offset\(\).top - 100  
        //  }, 0\);  
        //$\('.ml-subscribe-form-7556612 .ml-block-success'\).addClass\("animated zoomIn"\);  
    };                         
    jqueryDefer\(  
        function \(\) {  
            $\( document \).ready\(function\(\) {  
  
                 var freeMailList = \[  
                    'gmail.com',  
                    'yahoo.com',  
                    'hotmail.com',  
                    'yahoo.co.in',  
                    'aol.com',  
                    'abc.com',  
                    'xyz.com',  
                    'pqr.com',  
                    'rediffmail.com',  
                    'live.com',  
                    'outlook.com',  
                    'me.com',  
                    'msn.com',  
                    'ymail.com',  
                    'qq.com',  
                    'yandex',  
                    'mail.ru'  
                 \];   
  
                 var corporateEmailRegexString = '^\(\[\\w-\\.\]+@';  
                 for \(var i=0;i&lt;freeMailList.length;i++\) {  
                    var freeMail = freeMailList\[i\];  
                    corporateEmailRegexString += '\(?!'+freeMail+'\)';  
                 }                   
                 corporateEmailRegexString += '\(\[\\w-\]+\\.\)+\[\\w-\]{2,4}\)?$';  
                 var corporateEmailRegex = new RegExp\(corporateEmailRegexString\);  
  
                 function validateEmail\(email\) {  
                    if \(!email \|\| !email.length\) {  
                        return false;  
                    }  
                    return /^\(\[a-zA-Z0-9\_.+-\]\)+\@\(\(\[a-zA-Z0-9-\]\)+\.\)+\(\[a-zA-Z0-9\]\){2,40}$/.test\(email.trim\(\)\);  
                 }  
  
                 function validateCorporateEmail\(email\) {  
                    return corporateEmailRegex.test\(email.trim\(\)\);  
                 }  
  
                 $\('\#mlb2-7972110 button.primary'\).click\(function\(e\) {  
                        var emailContainer = $\('\#mlb2-7972110 .ml-field-email'\);  
                        var emailInput = emailContainer.find\('input\[type="email"\]'\);  
                        emailInput.keydown\(function\(\) {  
                            emailContainer.find\('.corporate-email-error'\).css\('display', 'none'\);  
                        }\);  
                        var email = emailInput.val\(\);  
                        emailContainer.removeClass\('ml-error'\);    
                        emailContainer.find\('.corporate-email-error'\).css\('display', 'none'\);  
                        if \(validateEmail\(email\)\) {  
                            // if \(!validateCorporateEmail\(email\)\) {   
                            //    emailContainer.addClass\('ml-error'\);    
                            //    emailContainer.find\('.corporate-email-error'\).css\('display', 'block'\);  
                            //    e.preventDefault\(\);  
                            //}  
                        }  
                 }\);  
  
                 $\('.subscribe-form .form-section .form-group input'\).addClass\("input--empty"\);  
                 $\('.subscribe-form .form-section .form-group input'\).on\('input', function\(\) {  
                      if\( !$\(this\).val\(\) \) {  
                         $\(this\).addClass\("input--empty"\);  
                      } else {  
                         $\(this\).removeClass\("input--empty"\);  
                      }  
                 }\);  
                 $.urlParam = function \(name\) {  
                    var results = new RegExp\('\[\?&\]' + name + '=\(\[^&\#\]\*\)'\).exec\(window.location.href\);  
                    return results ? results\[1\] : null;  
                 };                   
                 var deployType = $.urlParam\('deploy'\);  
                 if \(!deployType \|\| "premise" == deployType\) {  
                    $\('\#tab-on-premise'\).attr\("checked", "checked"\);  
                    var offset = !deployType ? 200 : 100;  
                    $\('html, body'\).animate\({  
                        scrollTop: $\('\#tab-on-premise'\).offset\(\).top - offset  
                      }, 0\);  
                 } else if \("cloud" == deployType\) {  
                    $\('\#tab-cloud'\).attr\("checked", "checked"\);   
                    $\('html, body'\).animate\({  
                        scrollTop: $\('\#tab-cloud'\).offset\(\).top - 100  
                      }, 0\);  
                 } else if \("trial" == deployType\) {  
                    $\('\#tab-trial'\).attr\("checked", "checked"\);   
                    $\('html, body'\).animate\({  
                       scrollTop: $\('\#tab-trial'\).offset\(\).top - 100  
                     }, 0\);  
                 }  
            }\);  
        }  
    \);  


