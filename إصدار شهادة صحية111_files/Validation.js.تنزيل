$(document).ready(function () {
    $('body').on("keypress", ".floatValue", function (e) {
        var charCode = (e.which) ? e.which : e.keyCode;
        if (charCode == 46 && $(this).val().indexOf(".") > 0)
            return false;
        if (charCode > 31 && (charCode == 47 || charCode < 46 || charCode > 57))
            return false;
    });
    $('body').on("keypress", ".intValue", function (e) {
        var charCode = (e.which) ? e.which : e.keyCode;
        if (charCode > 31 && (charCode < 48 || charCode > 57))
            return false;
    });
    $('body').on("change", ".required", validateRequired);

    $('body').on("change", ".rang", validateRange);
    $('body').on("change", ".regx", validateRegx);
    $('body').on("change", ".compar", validateCompar);
    $('body').on("click", ".validator", function () {
        return Validate($(this).data("vg"));
    });
});
function Validate(vg) {

    if (vg) {
        IsValid[vg] = true;
        $(".required[data-vg='" + vg + "']").each(validateRequired);
        $(".rang[data-vg='" + vg + "']").each(validateRange);
        $(".regx[data-vg='" + vg + "']").each(validateRegx);
        $(".compar[data-vg='" + vg + "']").each(validateCompar);

        $(this).data("valid", IsValid[vg]);
        return IsValid[vg];
    }
    else {
        IsValid["default"] = true;

        $(".required").each(validateRequired);
        $(".rang").each(validateRange);
        $(".regx").each(validateRegx);
        $(".compar").each(validateCompar);

        $(this).data("valid", IsValid["default"]);
        return IsValid["default"];
    }
}
function validateRequired() {

    if ($(this).parent().find('.mce-tinymce').length > 0) {
        var textArea = $(this).parent().find('.mce-edit-area');
        var editorContent = $(tinyMCE.get(this.id).getContent()).text().trim();
        if (editorContent == '' || editorContent == null || editorContent.length == 0) {
            textArea.addClass("tinymceInputRequiredError");

            if ($(this).data("vg")) {
                var gr = $(this).data("vg");
                IsValid[gr] = false;
            }
            else
                IsValid["default"] = false;
        }
        else {
            textArea.removeClass("tinymceInputRequiredError");
        }
    }
    else if ($(this).hasClass('select2')) {
        if (this.value == '' || this.value == null || this.value == "-1") {
            $(this).parent().find('.select2-selection').addClass("inputRequiredError");
            if ($(this).data("vg")) {
                var gr = $(this).data("vg");
                IsValid[gr] = false;
            }
            else
                IsValid["default"] = false;
        }
        else
            $(this).parent().find('.select2-selection').removeClass("inputRequiredError");
    }
    else if (this.value == '' || this.value == null || ($(this).is("select") && this.value == "-1") || this.value.length == 0) {
        $(this).addClass("inputRequiredError");

        if ($(this).data("vg")) {
            var gr = $(this).data("vg");
            IsValid[gr] = false;
        }
        else
            IsValid["default"] = false;
    }
    else
        $(this).removeClass("inputRequiredError");
}
function validateRange() {

    var val = parseInt(this.value);

    if (val < $(this).data("min") || val > $(this).data("max")) {
        $(this).addClass("inputRangeError");
        if ($(this).data("vg")) {
            var gr = $(this).data("vg");
            IsValid[gr] = false;
        }
        else
            IsValid["default"] = false;
    }
    else
        $(this).removeClass("inputRangeError");
}
function validateRegx() {

    if (this.value == '' || this.value == null || this.value.length == 0 || this.value.match($(this).data("regx"))) {
        $(this).removeClass("inputRegxError");
    }
    else {
        $(this).addClass("inputRegxError");
        if ($(this).data("vg")) {
            var gr = $(this).data("vg");
            IsValid[gr] = false;
        }
        else
            IsValid["default"] = false;
    }
}
function validateCompar() {

    var ctr = $(this).data("compar");
    if ($(this).val() == $(ctr).val())
        $(this).removeClass("inputComparError");
    else {
        $(this).addClass("inputComparError");
        if ($(this).data("vg")) {
            var gr = $(this).data("vg");
            IsValid[gr] = false;
        }
        else
            IsValid["default"] = false;
    }
}
var IsValid = {};

$(document).ready(function () {
    $('.nopaste').bind("paste", function (e) {
        return false;
    });
    $('body').on("keydown", ".max10", function () {
        if (event.keyCode != '8' && event.keyCode != '13' && event.keyCode != '46' && this.value.length + 1 > 10)
            event.returnValue = false;
    });
    $('body').on("keydown", ".max40", function () {
        if (event.keyCode != '8' && event.keyCode != '13' && event.keyCode != '46' && this.value.length + 1 > 40)
            event.returnValue = false;
    });
    $('body').on("keydown", ".max60", function () {
        if (event.keyCode != '8' && event.keyCode != '13' && event.keyCode != '46' && this.value.length + 1 > 60)
            event.returnValue = false;
    });
});