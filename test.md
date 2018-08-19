
## Random

### jQuery event bubbling, empty text in ckeditor 

  * event.stopPropagation(), event.stopImmediatePropagation(), event delegation (#LTN-749)
   `
   $(document).ready(function () {
        var selector = $('.node-form');
        var subselector = selector.find('.form-item'); // list-fieldset paragraphs-content form-item.
        var actions = subselector.find('.remove-item');

        $(subselector).on('click', '.remove-item', function(event) {
            if (event.target === this) {
                var editor = $(event.target).closest('tr').find('textarea').attr('id');
                CKEDITOR.instances[editor].setData('');
                $(event.target).closest('tr').hide();
            }
            else {
                unbind();
            }
        });

    });
    `

## 2.5.0

### Bug Fixes

  * Add `jekyll-feed` plugin in config (#228)

### Minor Enhancements

  * Stick footer for short posts (#223)
  * Consolidate trigger SVG paths (#148)

## 2.4.1

### Bug Fixes

  * Reintroduce removed social includes for backwards compatibility (#217)
