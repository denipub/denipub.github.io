
## Random

### Week 13.8-19.8.2018
#### jQuery prevent event bubbling, emptying text in ckeditor 

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


#### Drupal button for removing fields in multi value field inside Paragraphs in article node

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

### Week 20.8-26.8.2018

#### Get taxonomy vacabulary of referenced taxonomy term (get field definition/field settings of referenced entity)

                // Hide Tags for News article type.
                if (isset($form['field_tags']) && strpos($entity->bundle(), 'news') !== FALSE) {
                  $field_tags = $entity->get('field_tags');
                  kint($field_tags);
                  kint($field_tags->getFieldDefinition());
                  $ref_field_settings = $field_tags->getFieldDefinition()->get('settings');
                  // target_bundles is the vocabulary
                  kint($ref_field_settings['handler_settings']['target_bundles']);
                  //$form['field_tags']['#access'] = FALSE;
                }



#### Change tabs, menu

use function hook_menu_local_tasks_alter to change tabs
use function template_preprocess_menu_local_action to change menu (admin toolbar??)


### Week 27.8-2.9.2018

#### Entity Browser translation

* URL not workong (routing problem) - user this addresses to get to translation screens:

admin/config/content/entity_browser/{entity_browser}/general/translate/{langcode}/add
admin/config/content/entity_browser/{entity_browser}/general/translate/{langcode}/edit

### Week 22.10-28.10.2018

#### Twigg

var_dump() in twig template:  {{ dump(row) }}


#### widget form alter (add css class to multi value field inside fieldset/details)

        /**
         * Implements hook_field_widget_WIDGET_TYPE_form_alter().
         */
        function ltn_types_field_widget_entity_browser_entity_reference_form_alter(&$element, FormStateInterface $form_state, $context)         {
          // Add css class to image fields for css positioning.
          if ($context['items']->getName() == 'field_image') {
            $element['#attributes']['class'][] = 'image-field';
          }
        }



## 2.5.0

  * Add `jekyll-feed` plugin in config (#228)

### Minor Enhancements

  * Stick footer for short posts (#223)
  * Consolidate trigger SVG paths (#148)

## 2.4.1

### Bug Fixes

  * Reintroduce removed social includes for backwards compatibility (#217)
