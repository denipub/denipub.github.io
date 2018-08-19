
## Random

#### Week 13.8-19.8.2018
### jQuery prevent event bubbling, emptying text in ckeditor 

  * KW: event.stopPropagation(), event.stopImmediatePropagation(), event delegation (#LTN-749)


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

(https://stackoverflow.com/questions/7448860/how-to-stop-event-propagation-when-using-delegate)                


### Drupal add button to multi value field inside Paragraphs in article node

MODULENAME.module inside function MODULENAME_form_node_form_alter(&$form, FormStateInterface $form_state, $form_id) {

                $i = 0;
                foreach ($form['field_paragraphs']['widget']['0']['subform']['field_list_items']['widget'] as $delta => $item) {
                  if (is_numeric($delta) && $item['#base_type'] == 'textarea') {

                    $form['field_paragraphs']['widget']['0']['subform']['field_list_items']['widget'][$i]['remove_item'] = [
                      '#type' => 'button',
                      '#value' => t('x', [], ['context' => 'ltn']),
                      '#title' => t('Remove item', [], ['context' => 'ltn']),
                      '#name' => 'remove-item',
                      '#attributes' => [
                        'onclick' => 'return (false);',
                        'class' => [
                          'remove-item', 'button--small',
                        ],
                      ],
                    ];
                    $i++;
                  }
                }

## 2.5.0

### Bug Fixes

  * Add `jekyll-feed` plugin in config (#228)

### Minor Enhancements

  * Stick footer for short posts (#223)
  * Consolidate trigger SVG paths (#148)

## 2.4.1

### Bug Fixes

  * Reintroduce removed social includes for backwards compatibility (#217)
