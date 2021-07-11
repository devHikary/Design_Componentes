- Two way data Binding

    Two way data binding só funciona pq as duas propriedades tem o mesmo nome (output  acrescido o sufixo **Change**)

    ```tsx
    [(value)]="yesNoAnswer"
    ```

- O `FormBuilder` vai auxiliar a criar a propriedade form
- `ngSubmit` se caso tiver algum erro de validação no `submit()` a página não será atualizada.
- É preciso associar o campo do formulário com a propriedade

    ```tsx
    formControlName = "yesNoAnswer"
    ```

- Interface `ControlValueAccessor`: Quando criamos um componente para o formulário é preciso implementar o `control value access` para "ensinar" ao `formGroup` como o componente deve se comportar.
    - Os componentes padrões do HTML já possuem essa interface implementada, por isso não precisamos nos preocupar
- `NG_VALUE_ACCESSOR` é usada para configurar a sincronização com formControl.
- É um injection token que marca nosso componente para que seja injetado dentro da infraestrutura do formGroup.
- O `forwardRef` é usado quando o `injection token` que precisamos referenciar, que é o `NG_VALUE` é declarado, mas ainda não é definido.
- No `activate`, chamar o `writeValue` que vai mudar o valor da propriedade do componente e ainda vai notificar o angular que ele tem que propagar uma mudança.

    ```tsx
    public writeValue(value: string): void {
        this.value = value;
        this.onChange(this.value);
        this.valueChange.emit(this.value);
      }
    ```

    ```tsx
    public activate(value: string): void{
        this.writeValue(value);
      }
    ```
- `role`: permite aplicar semântica e elemento não semânticos do HTML, inclusive mudar a semântica padrão de elementos já existentes.
- Biblioteca para criar um id único

    ```tsx
    npm install uuid@8.3.0
    ```

- Se for utilizar uma biblioteca utilitária em todos os componentes, é importante criar uma camada/ um  service para essa biblioteca. Assim, se caso um dia, mudarmos essa biblioteca será preciso alterar em apenas um lugar.


## Ferramenta para teste de Acessibilidade

- Plugin do Chrome : ChromeVox Classic Extension

- [https://www.w3.org/TR/wai-aria-practices-1.1/](https://www.w3.org/TR/wai-aria-practices-1.1/)
