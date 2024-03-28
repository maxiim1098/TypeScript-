
# Project Title

TypeScript Абстрактные классы


Абстрактные классы с ключевым словом abstract они похожи на обычные классы за тем исключением, что мы не можем создать напрямую объект обстрактного класса


# Пример

enum TypeControl {
    Input = 0,
    Select = 1
}

abstract class Control {
    private _type: TypeControl;

    public get name(): string {
        let result = "";
        switch (this._type) {
            case TypeControl.Input:
                result = "Ввод текста"
                break
            case TypeControl.Select:
                result = "Выберите значение из выпадающего списка"
                break
        }
        return result
    }

    @param tc
    constructor(tc: TypeControl){
        this._type = tc
    }

    public abstract getInfo(): string

    public abstract getName(): string
}

class TextBox extends Control {
    private _maxlenght: number
    public get maxlenght(): number {
        return this._maxlenght
    }
    @param m
    constructor(m: number){
        super(TypeControl.Input)
        this._maxlenght = m
    }
}

class SelectBox extends Control {

    private _items: Array<string>

    constructor(items: Array<string> = []){
        super(TypeControl.Select)
        this._items = items
    }
    public getInfo(): string {
        let str = this._items.reduce((d, c, array) => {
            return d + `;` + c
        })
        return `Control: name = ${this.name} | SelectBox: Варианты для выбора`
    }
}

let textbox = new TextBox(10)
console.log((textbox as Control).getInfo())

let selectbox = new SelectBox(["Первый", "Второй", "Третий"])
console.log((selectbox as Control).getInfo())

// let control = new Control(null)

