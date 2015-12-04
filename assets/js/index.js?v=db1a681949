var interval;

$(function() {

  var open = false;

  /** reponsive videos **/
  $(".post-cover, .post-content").fitVids();

  $(".posts .post-cover").each(function() {

    var available = false;
    // image cover
    var $cover = $("img", $(this));
    if($cover && $cover.length == 1) {
      $(this).html(
              "<img src='" + $cover.attr("src") + "' />" +
                  "<div class='post-image-overlay'>" +
                    "<a href='" + $cover.attr("src") + "' class='preview' data-lightbox='image-" + $(this).data("post") + "'><span class='fa fa-search'></span></a>" +
                    "<a href='" + $(this).data("url") + "' class='link'><span class='fa fa-link'></a></span>" +
                  "</div>").removeClass("hide");
      available = true;
    }

    // video cover
    var $videoCover = $(".fluid-width-video-wrapper", $(this));
    if($videoCover && $videoCover.length == 1) {
      $(this).removeClass("hide");
      available = true;
    }

    // soudcloud cover
    var $iframeCover = $("iframe[src*='soundcloud.com']", $(this));
    if($iframeCover && $iframeCover.length == 1) {
      $(this).removeClass("hide");
      available = true;
    }

    // blog cover image
    var blogCoverImage = $(this).data("image");
    if(blogCoverImage && !available) {
      $(this).html("<img src='" + blogCoverImage + "' />");
      $(this).removeClass("hide");
    }

    $(this).closest("article").removeClass("non-visible").addClass("animated fadeIn");
  });

  /* image lightbox */
  $(".post-content").imagesLoaded(function() {
    $(".post-content img").each(function() {
      var height = $(this).height();
      var width = $(this).width();
      $(this).wrap($("<div class='post-image'></div>").css("height", height).css("width", width));
      $(this).after("<a href='" + $(this).attr("src") + "' data-lightbox='image-post'><div class='post-image-overlay'></div></a>")
    });
  });

  $(window).resize(function() {
    resizeImage();
  });

  $('.post').resize(function() {
    resizeImage();
  });

  // responsive google map
  $("iframe[src*='google.com']").each(function() {
    $(this).wrap($("<div class='google-map'></div>"));
  });

  $('.more a').click(function(e){
    e.preventDefault();
    $('html, body').animate({
      scrollTop: $( $.attr(this, 'href') ).offset().top
    }, 500);
    return false;
  });

  $(".blog-menu, .blog-menu-close").click(function(e) {
    e.preventDefault();
    $("body").toggleClass("open");
    var $sidebar = $('#sidebar-wrapper');
    $sidebar.toggleClass('show');
    open = !open;
    if(!open) {
      $sidebar.css('display', 'block');
      setTimeout(function() {
        $sidebar.css('display', 'none');
      }, 400);
    }
    interval = setInterval(resizeImage, 500);
  });

    // scroll up plugin
  $().showUp('.js-scroll-up', {
    upClass: '{{upClass}}',
    downClass: '{{downClass}}'
  });


  if($("#disqus_thread").length > 0) {
    // disqus
    (function() {
      var dsq = document.createElement('script'); dsq.type = 'text/javascript'; dsq.async = true;
      dsq.src = '//' + disqus_shortname + '.disqus.com/embed.js';
      (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(dsq);
    })();
  }

});


function resizeImage() {
  if(interval) {
    clearInterval(interval);
    interval = null;
  }
  $(".post-content img").each(function() {
    $(this).parent().css("height", "").css("width", "");
    var height = $(this).height();
    var width = $(this).width();
    $(this).parent().css("height", height).css("width", width);
  })
}
