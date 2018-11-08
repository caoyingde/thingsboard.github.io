---
layout: docwithnav
title: Contact us
---

# contact-us

  
  
    function validateContactForm\(form\) {  
        var firstName = $\('input\[name=first-name\]', form\).val\(\);  
        var lastName = $\('input\[name=last-name\]', form\).val\(\);  
        var email = $\('input\[name=email\]', form\).val\(\);  
        var company = $\('input\[name=company\]', form\).val\(\);  
        var subject = $\('select\[name=subject\]', form\).val\(\);  
        var message = $\('textarea\[name=message\]', form\).val\(\);  
  
        if \(!validateValue\('First Name', firstName\)\) {  
            return false;  
        }  
        if \(!validateValue\('Last Name', lastName\)\) {  
            return false;  
        }  
        if \(!validateValue\('Email Address', email\)\) {  
            return false;  
        }  
  
        var emailExp = /^\[a-zA-Z0-9.\_%-\]+@\[a-zA-Z0-9.-\]+\.\[a-zA-Z\]{2,4}$/;  
        if\(email.match\(emailExp\)==null\) {  
            window.alert\("Entered Email Address is not valid."\);  
            return false;   
        }  
  
        if \(!validateValue\('Company', company\)\) {  
            return false;  
        }  
  
        if \(isEmpty\(subject\)\) {  
            window.alert\("Please select Subject."\);  
            return false;  
        }  
  
        /\*if \(subject === 'Please Select'\) {  
            window.alert\("Please select Subject."\);  
            return false;  
        }\*/  
  
        if \(!validateValue\('Message', message\)\) {  
            return false;  
        }  
        return true;  
    }  
  
    function validateValue\(name, val\) {  
        if \(isEmpty\(val\)\) {  
            window.alert\("Please fill '" + name + "' field."\);  
            return false;  
        }  
        return true;  
    }  
  
    function isEmpty\(val\) {  
        return val === undefined \|\| val.trim\(\).length == 0;  
    }  
  


First Name\* 

Last Name\* 

Email Address\* 

Company\* Technical SupportThingsBoard ProductsDeployment OptionsTrainingProfessional ServicesPartnershipPress or Analyst InquiryGeneral FeedbackOther

Subject\*

Message\*   

  
  
    var contactform =  document.getElementById\('contact-form'\);  
    contactform.setAttribute\('action', 'https://formspree.io/' + 'support' + '@' + 'thingsboard' + '.' + 'io'\);  
  
    jqueryDefer\(  
        function \(\) {  
            $\( document \).ready\(function\(\) {  
                 $\('html, body'\).animate\({  
                            scrollTop: $\('\#contact-form'\).offset\(\).top - 200  
                          }, 0\);  
                 $\('\#contact-form .form-element .form-control'\).addClass\("input--empty"\);  
                 $\('\#contact-form .form-element .form-control'\).on\('input', function\(\) {  
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
                 var subjectValue = $.urlParam\('subject'\);  
                 if \(subjectValue != undefined && subjectValue.trim\(\).length &gt; 0\) {                      
                    $\('\#contact-form select\[name=subject\]'\).val\(decodeURIComponent\(subjectValue\)\);  
                    $\('\#contact-form select\[name=subject\]'\).removeClass\("input--empty"\);  
                 }  
            }\);  
        }  
    \);  


