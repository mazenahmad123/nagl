// ==============================================================
// loading
// ==============================================================
$(window).on("load", function () {
    $('body').addClass('loaded');
    $("#preloader-logo").fadeOut();
});
$(document).on('click', '.btn-checking', function () {
    $('body').addClass('loaded-checking');

    setTimeout(function () { $('body').removeClass('loaded-checking'); }, 3000);

});
$('[data-toggle="tooltip"]').tooltip({
    boundary: 'window'
})
$(function () {
    "use strict";
    // ==============================================================
    // Parsley
    // ==============================================================
    if ($('form').length) {
        var attr = $('form').attr('data-parsley-validate');
        // For some browsers, `attr` is undefined; for others,
        // `attr` is false.  Check for both.
        if (typeof attr !== typeof undefined && attr !== false) {
            window.Parsley.on('form:validated', function () {
                $('select').on('select2:select', function (evt) {
                    $(this).parsley().validate();
                });
            });
        }
    }
    // ==============================================================
    // top navbar hover
    // ==============================================================
    $(".top-navbar  .navbar-nav .nav-link , .top-navbar  .navbar-nav .dropdown-menu").on({
        mouseenter: function () {
            $(this).addClass('hover');
            $(this).closest('nav').addClass('nav-link-hover');
        },
        mouseleave: function () {
            $(this).removeClass('hover');
            $(this).closest('nav').removeClass('nav-link-hover');
        }
    });
    // ==============================================================
    // stop navbar close on click
    // ==============================================================

    jQuery(document).on('click', '.top-navbar .dropdown-menu', function (e) {
        e.stopPropagation();
    });
    // ==============================================================
    // transfer-service-modal
    // ==============================================================
    $('.transfer-service-modal').on('show.bs.modal', function () {
        // $('.service-modal:not(.transfer-service-modal)').modal('hide');
        $('body').addClass('modal-open');
        // setTimeout(function() {
        //   $('body').addClass('modal-open');
        // }, 500);
    })
    $('.transfer-service-modal').on('hide.bs.modal', function () {
        $('.service-modal:not(.transfer-service-modal)').modal('hide');
    })
    // ==============================================================
    // header open dropdown event
    // ==============================================================
    $('.site-header .dropdown ').on('show.bs.dropdown', function () {
        $('body').addClass('menu-dropdown-open');
    })

    $('.site-header .dropdown ').on('hide.bs.dropdown', function () {
        $('body').removeClass('menu-dropdown-open');
    })
    // ==============================================================
    //   $.scrollIt();
    // ==============================================================
    if ($('.scrollIt').length) {
        $.scrollIt();
    }
    // ==============================================================
    // Fixed header
    // ==============================================================
    fixed_header();
    $(window).scroll(function () {
        fixed_header();
    });
    function fixed_header() {
        var ht = $('.site-header').height();
        var st = $(window).scrollTop();
        var sf = ht + 200;
        var sb = 800;
        if (st > ht) {
            $('.site-header').addClass('nav-fixed');
            $('.top-navbar').addClass('nav-fixed');
            $('.page-top-fixed').addClass('nav-fixed');
        } else {
            $('.site-header').removeClass('nav-fixed');
            $('.top-navbar').removeClass('nav-fixed');
            $('.page-top-fixed').removeClass('nav-fixed');
        }
        if (st > sf) {
            $('.site-header').addClass('fixed');
            $('.top-navbar').addClass('fixed');
            // $('.page-top-fixed').addClass('fixed');

        } else {
            $('.site-header').removeClass('fixed');
            $('.top-navbar').removeClass('fixed');
            // $('.page-top-fixed').removeClass('fixed');
        }

    }
    // ==============================================================
    // choose-custom-date-type
    // ==============================================================
    $('.choose-custom-date-type input').on('change', function () {

        $(this).closest('.date-type-cont').find('.collapse').collapse('hide');
        if ($(this).attr('data-date-type') === "hijri") {
            $(this).closest('.date-type-cont').find($(this).attr('data-target')).collapse('hide');
            $(this).closest('.date-type-cont').find($(this).attr('data-target')).collapse('show');
        } else {
            $(this).closest('.date-type-cont').find($(this).attr('data-target')).collapse('hide');
            $(this).closest('.date-type-cont').find($(this).attr('data-target')).collapse('show');
        }
    });
    // ==============================================================
    // select2
    // ==============================================================
    // Adding placeholder for search input
    if ($("select").length) {
        $(function () {
            'use strict'
            var Placeholder = 'ابحث هنا ';
            if ($('html').attr('dir') == "ltr") {
                Placeholder = 'Search options';
            }
            // Basic with search
            $('.select2:not(.select2-icon)').select2({
                language: $('html').attr('lnag'),
                dir: $('html').attr('dir'),
                searchInputPlaceholder: Placeholder,
                width: "100%"
            });
            function formatState(state) {
                if (!state.id) {
                    return state.text;
                }
                var $state = $(
                    '<span><i class="' + state.element.value.toLowerCase() + ' "  /> ' + state.text + '</span>'
                );
                return $state;
            };
            // Basic with search
            $('.select2-icon').select2({
                language: $('html').attr('lnag'),
                dir: $('html').attr('dir'),
                searchInputPlaceholder: Placeholder,
                templateResult: formatState,
                width: "100%"
            });

        });
    }
    //====================================
    //     file upload
    //====================================
    function readURL(input, elem) {
        if (input.files && input.files[0]) {
            var reader = new FileReader();
            reader.onload = function (e) {
                $(elem).attr("src", e.target.result);
            }
            reader.readAsDataURL(input.files[0]);
        }
    }
    $(document).on('change', '.form-control-upload input[type="file"]', function () {

        if (this.files.length > 0) {
            var file = this.files[0];
            var fileType = file["type"];
            var validImageTypes = ["image/gif", "image/jpeg", "image/png"];

            if ($.inArray(fileType, validImageTypes) < 0 == false) {
                var preview_elem = $(this).attr('data-img-preview');
                $(this).parents('.form-control-upload').addClass('active');
                $(this).parents('.form-control-upload').next('.upload-file-preview').removeClass('d-none');
                //$(this).parents('.form-control-upload').find('.upload-info').html($(this).val());
                $(this).parents('.form-control-upload').find('.upload-info').html(file.name);
                $(this).parents('.form-control-upload').find('a').remove();

                readURL(this, preview_elem);

            } else if ($(this).val().length > 0) {
                $(this).parents('.form-control-upload').addClass('active');
                $(this).parents('.form-control-upload').next('.upload-file-preview').addClass('d-none');
                $(this).parents('.form-control-upload').find('.upload-info').html(file.name);
                //$(this).parents('.form-control-upload').find('.upload-info').html($(this).val());

            } else {
                $(this).parents('.form-control-upload').removeClass('active');
                $(this).parents('.form-control-upload').find('.upload-info').html('اختر ملف ');
            }
        }
        else {
            $(this).parents('.form-control-upload').removeClass('active');
            $(this).parents('.form-control-upload').find('.upload-info').html('اختر ملف ');
        }
    });

    //====================================
    //     file upload preview close
    //====================================
    $(document).on('click', '.upload-file-preview .icon-close', function () {
        $(this).parent().prev('.form-control-upload').find('input[type="file"]').val('');
        $(this).parent().prev('.form-control-upload').find('.upload-info').text($(this).parent().prev('.form-control-upload').find('input[type="file"]').attr("title"));
        $(this).parent().addClass('d-none');
    });
    //====================================
    //    agreement-modal
    //====================================
    var global_modal_checkbox_id = "";
    $('#agreement-modal').on('show.bs.modal', function (e) {
        global_modal_checkbox_id = $(e.relatedTarget).closest('.custom-control').find('[data-target="agreement-modal-checkbox"]').attr("id");

    })
    $('#agreement-modal .agreement-modal-btn').on('click', function () {

        $('#agreement-modal').modal('hide');
        $("#" + global_modal_checkbox_id).prop('checked', true);
        $("#" + global_modal_checkbox_id).removeAttr('disabled');

        if ($('.activity-isic-row').length) {
            $('.activity-isic-row').addClass('active');
        }
    });
    $('.activity-isic-row .btn-add-more-isic').on('click', function () {
        $(this).closest('.activity-isic-row').find('.collapse').addClass('show');
    });
    //====================================
    //    add next prev in stepanchor
    //====================================
    if ($('.page-top-fixed .step-anchor').length) {
        $('.page-top-fixed .step-anchor').find('.nav-item.active').next().addClass('next');
        $('.page-top-fixed .step-anchor').find('.nav-item.active').prev().addClass('prev');
    }
    //====================================
    //    get-geo-location check
    //====================================
    $('.get-geo-location .check-geo-loaction-btn').on('click', function () {

        $(this).closest('.get-geo-location').find('.form-control').each(function () {
            $(this).prop('disabled', true);
        });
        $(this).closest('.get-geo-location').find('.get-geo-location-btn').removeClass('d-none');
        $(this).closest('.get-geo-location').find('.check-geo-loaction-btn').addClass('d-none');

    });
    //====================================
    //choose-service-type collapse
    //====================================
    $('.choose-service-type.top-level .custom-control-label').on('click', function () {

        if ($(this).hasClass('disabled') || $(this).parent().hasClass('disabled'))
            return;
        var service = $(this).closest('.choose-service-type');

        service.find('.custom-control-label').removeClass('active');
        $(this).addClass('active');
        var target = $(this).attr('data-target');

        service.find('.accordion  > .collapse').removeClass('show');
        $(target).addClass('show');
    });
    //====================================
    // rate
    //====================================
    $(document).on("click mouseup touchstart", ".rate-cont .rate-item", function () {
        $(this).addClass('active');
        $(this).prevAll().addClass('active');
        $(this).nextAll().removeClass('active');
        $(this).closest('.rate-cont').attr('data-rate', $(this).index() + 1);

    });
    //====================================
    // select2 on change
    //====================================
    $('.has-agreement-modal').on("select2:selecting", function (e) {
        //$('#agreement-modal').modal('show');
    });

});
