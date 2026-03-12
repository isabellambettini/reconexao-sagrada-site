import React from "react";
import { motion } from "framer-motion";
import {
  ShoppingBag,
  Instagram,
  Phone,
  Sparkles,
  MoonStar,
  Flame,
  Flower2,
  BookOpen,
  Gem,
  CalendarDays,
  Clock3,
  MapPin,
  Heart,
} from "lucide-react";
import {
  Card,
  CardContent,
  CardHeader,
  CardTitle,
  CardDescription,
} from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Badge } from "@/components/ui/badge";
import {
  Dialog,
  DialogContent,
  DialogDescription,
  DialogHeader,
  DialogTitle,
  DialogTrigger,
} from "@/components/ui/dialog";

const BRAND = {
  name: "Reconexão Sagrada",
  instagramHandle: "@reconexaosagradaa",
  instagram: "https://instagram.com/reconexaosagradaa",
  whatsapp: "5511973707789",
  city: "São Paulo • SP",
  circle: {
    theme: "Poder em Expansão",
    date: "07/03",
    time: "19h30",
    location: "Rua Ibitirama, 963 — Vila Prudente",
    price: "R$ 120,00",
  },
};

function wa(message: string) {
  return `https://wa.me/${BRAND.whatsapp}?text=${encodeURIComponent(message)}`;
}

const products = [
  {
    name: "Planners por encomenda",
    subtitle: "Capas, miolos e personalização",
    price: "Sob consulta",
    image:
      "https://images.unsplash.com/photo-1517842645767-c639042777db?auto=format&fit=crop&w=1200&q=80",
    icon: BookOpen,
    message: "Olá! Quero encomendar um planner da Reconexão Sagrada.",
  },
  {
    name: "Cadernos místicos",
    subtitle: "Escrita, alma e propósito",
    price: "Sob consulta",
    image:
      "https://images.unsplash.com/photo-1455390582262-044cdead277a?auto=format&fit=crop&w=1200&q=80",
    icon: MoonStar,
    message: "Olá! Quero encomendar um caderno místico da Reconexão Sagrada.",
  },
  {
    name: "Escalda-pés ritualístico",
    subtitle: "Autocuidado e renovação",
    price: "Sob consulta",
    image:
      "https://images.unsplash.com/photo-1544161515-4ab6ce6db874?auto=format&fit=crop&w=1200&q=80",
    icon: Flower2,
    message: "Olá! Quero saber mais sobre os escalda-pés da Reconexão Sagrada.",
  },
  {
    name: "Kit 2 velas consagradas",
    subtitle: "Ritual e intenção",
    price: "Sob consulta",
    image:
      "https://images.unsplash.com/photo-1603006905003-be475563bc59?auto=format&fit=crop&w=1200&q=80",
    icon: Flame,
    message: "Olá! Quero montar um kit com 2 velas consagradas.",
  },
  {
    name: "Ecobags personalizadas",
    subtitle: "Arte, praticidade e identidade",
    price: "Sob consulta",
    image:
      "https://images.unsplash.com/photo-1542291026-7eec264c27ff?auto=format&fit=crop&w=1200&q=80",
    icon: ShoppingBag,
    message: "Olá! Quero encomendar uma ecobag personalizada da Reconexão Sagrada.",
  },
  {
    name: "Saquinhos e acessórios",
    subtitle: "Detalhes com significado",
    price: "Sob consulta",
    image:
      "https://images.unsplash.com/photo-1617038220319-276b7c3f6d84?auto=format&fit=crop&w=1200&q=80",
    icon: Gem,
    message: "Olá! Quero conhecer os saquinhos e acessórios da Reconexão Sagrada.",
  },
];

function EncomendaDialog() {
  return (
    <Dialog>
      <DialogTrigger asChild>
        <Button className="rounded-full bg-white/80 text-[#7a5aa8] hover:bg-white">
          Como funciona a encomenda
        </Button>
      </DialogTrigger>
      <DialogContent className="rounded-[28px] border-none bg-white/95">
        <DialogHeader>
          <DialogTitle className="text-xl text-[#6e4f95]">
            Como funciona a encomenda
          </DialogTitle>
          <DialogDescription className="text-slate-600">
            Um processo leve, delicado e personalizado para criar algo com a sua energia.
          </DialogDescription>
        </DialogHeader>

        <div className="space-y-3 text-sm text-slate-700">
          {[
            ["1. Escolha a proposta", "Você define se deseja planner, caderno, kit, ecobag ou outro item disponível."],
            ["2. Defina o estilo", "Pode escolher cores, referências, frases, elementos místicos e a intenção do material."],
            ["3. Ajuste dos detalhes", "Alinhamos capa, miolo, personalização, acabamento e proposta visual."],
            ["4. Prazo e pagamento", "Informamos o prazo de produção, valor final e forma de pagamento."],
            ["5. Entrega ou retirada", "Após a finalização, combinamos entrega ou retirada da melhor forma para você."],
          ].map(([title, text]) => (
            <div key={title} className="rounded-2xl border border-[#efe2f4] bg-[#fffafc] p-4">
              <div className="font-medium text-[#6e4f95]">{title}</div>
              <div className="mt-1 text-slate-600">{text}</div>
            </div>
          ))}

          <div className="flex flex-col gap-2 pt-2 sm:flex-row">
            <Button asChild className="rounded-full bg-[#a988d8] text-white hover:bg-[#9670cb]">
              <a href={wa("Olá! Quero encomendar um produto personalizado da Reconexão Sagrada.")} target="_blank" rel="noreferrer">
                Quero encomendar
              </a>
            </Button>
            <Button asChild variant="outline" className="rounded-full border-[#d8c0f3] text-[#7a5aa8]">
              <a href={wa("Olá! Tenho uma dúvida sobre as encomendas da Reconexão Sagrada.")} target="_blank" rel="noreferrer">
                Tirar dúvidas
              </a>
            </Button>
          </div>
        </div>
      </DialogContent>
    </Dialog>
  );
}

function ProductCard({ p, index }: { p: (typeof products)[number]; index: number }) {
  const Icon = p.icon;

  return (
    <motion.div
      initial={{ opacity: 0, y: 18 }}
      animate={{ opacity: 1, y: 0 }}
      transition={{ duration: 0.35, delay: index * 0.05 }}
    >
      <Card className="h-full overflow-hidden rounded-[28px] border-white/50 bg-white/85 shadow-[0_18px_50px_rgba(88,58,122,0.10)] backdrop-blur">
        <div className="relative h-60 overflow-hidden">
          <img src={p.image} alt={p.name} className="h-full w-full object-cover" />
          <div className="absolute inset-0 bg-gradient-to-t from-black/20 via-transparent to-transparent" />
          <div className="absolute left-4 top-4 rounded-full bg-white/90 p-3 text-[#7b5bc7] shadow-sm">
            <Icon className="h-5 w-5" />
          </div>
        </div>

        <CardHeader className="space-y-2">
          <CardTitle className="text-lg text-[#5f476f]">{p.name}</CardTitle>
          <CardDescription className="text-sm font-medium text-[#c18bb5]">
            {p.subtitle}
          </CardDescription>
        </CardHeader>

        <CardContent className="space-y-4">
          <div className="text-sm font-semibold text-[#7b5bc7]">{p.price}</div>
          <Button asChild className="w-full rounded-full bg-[#a988d8] text-white hover:bg-[#9670cb]">
            <a href={wa(p.message)} target="_blank" rel="noreferrer">
              Pedir pelo WhatsApp
            </a>
          </Button>
        </CardContent>
      </Card>
    </motion.div>
  );
}

export default function SiteReconexao() {
  return (
    <div className="min-h-screen bg-[radial-gradient(circle_at_top_left,_rgba(255,255,255,0.8),_transparent_30%),linear-gradient(135deg,#fdf1f7_0%,#f4ecff_52%,#fff8ea_100%)] text-slate-800">
      <section className="relative overflow-hidden bg-[linear-gradient(135deg,rgba(244,191,214,0.96),rgba(203,184,235,0.96),rgba(239,220,171,0.90))] text-white">
        <div className="absolute inset-0 opacity-20">
          <div className="absolute left-[-80px] top-[-80px] h-72 w-72 rounded-full bg-white blur-3xl" />
          <div className="absolute bottom-[-100px] right-[-60px] h-80 w-80 rounded-full bg-white blur-3xl" />
        </div>

        <div className="relative mx-auto max-w-6xl px-4 py-16 sm:py-20">
          <div className="mb-6 flex flex-wrap gap-3">
            <Badge className="rounded-full bg-white/20 px-4 py-1.5 text-white hover:bg-white/20">
              <Sparkles className="mr-2 h-3.5 w-3.5" /> Catálogo & Vivências
            </Badge>
            <Badge className="rounded-full bg-white/10 px-4 py-1.5 text-white hover:bg-white/10">
              {BRAND.city}
            </Badge>
          </div>

          <div className="grid items-center gap-10 lg:grid-cols-[1.2fr_.8fr]">
            <div>
              <motion.div
                initial={{ opacity: 0, y: 24 }}
                animate={{ opacity: 1, y: 0 }}
                transition={{ duration: 0.45 }}
              >
                <div className="mb-5 flex items-center gap-4">
                  <div className="rounded-2xl bg-white/15 p-3 backdrop-blur">
                    <MoonStar className="h-8 w-8" />
                  </div>
                  <div>
                    <h1 className="text-4xl font-semibold tracking-tight sm:text-5xl">
                      {BRAND.name}
                    </h1>
                    <p className="mt-2 max-w-2xl text-sm leading-relaxed text-white/90 sm:text-base">
                      Um espaço de reconexão, intenção e criação com alma — onde produtos artesanais e vivências se encontram para despertar beleza, presença e significado.
                    </p>
                  </div>
                </div>

                <div className="flex flex-wrap gap-3">
                  <Button asChild className="rounded-full bg-white text-[#7a5aa8] hover:bg-white/95">
                    <a href="#catalogo">Ver catálogo</a>
                  </Button>
                  <Button asChild variant="outline" className="rounded-full border-white/60 bg-transparent text-white hover:bg-white/10">
                    <a href="#circulo">Círculo Sagrado</a>
                  </Button>
                  <Button asChild variant="outline" className="rounded-full border-white/60 bg-transparent text-white hover:bg-white/10">
                    <a href={wa("Olá! Quero falar com a Reconexão Sagrada.")} target="_blank" rel="noreferrer">
                      <Phone className="mr-2 h-4 w-4" /> WhatsApp
                    </a>
                  </Button>
                </div>

                <div className="mt-8 flex flex-wrap gap-3 text-sm text-white/95">
                  <span className="rounded-full bg-white/10 px-4 py-2 backdrop-blur">Planners por encomenda</span>
                  <span className="rounded-full bg-white/10 px-4 py-2 backdrop-blur">Kits e velas consagradas</span>
                  <span className="rounded-full bg-white/10 px-4 py-2 backdrop-blur">Ecobags e acessórios</span>
                </div>
              </motion.div>
            </div>

            <motion.div
              initial={{ opacity: 0, scale: 0.96 }}
              animate={{ opacity: 1, scale: 1 }}
              transition={{ duration: 0.45, delay: 0.1 }}
            >
              <Card className="overflow-hidden rounded-[32px] border-white/40 bg-white/18 p-0 text-white shadow-[0_20px_80px_rgba(63,35,99,0.18)] backdrop-blur-md">
                <div className="border-b border-white/20 px-6 py-5">
                  <div className="text-sm font-medium uppercase tracking-[0.2em] text-white/80">
                    Essência & delicadeza
                  </div>
                  <div className="mt-2 text-2xl font-semibold">
                    Uma presença elegante e mística
                  </div>
                </div>
                <div className="space-y-4 px-6 py-6 text-sm text-white/90">
                  <div>• Delicadeza, espiritualidade e beleza sutil</div>
                  <div>• Encomendas personalizadas com alma e intenção</div>
                  <div>• Um espaço que une autocuidado, criação e reconexão</div>
                </div>
              </Card>
            </motion.div>
          </div>
        </div>
      </section>

      <section id="circulo" className="mx-auto max-w-6xl px-4 py-16">
        <div className="mb-8 flex flex-col gap-4 md:flex-row md:items-end md:justify-between">
          <div>
            <div className="mb-3 inline-flex rounded-full bg-white/70 px-4 py-2 text-sm font-medium text-[#7a5aa8] shadow-sm">
              <MoonStar className="mr-2 h-4 w-4" /> Vivência especial
            </div>
            <h2 className="text-3xl font-semibold tracking-tight text-[#5f476f]">
              Círculo Sagrado
            </h2>
            <p className="mt-2 max-w-2xl text-sm leading-relaxed text-slate-600 sm:text-base">
              Um encontro de presença, partilha e expansão feminina para mulheres que desejam pausar, sentir e se reconectar com sua potência interior.
            </p>
          </div>
          <Button asChild className="rounded-full bg-[#a988d8] text-white hover:bg-[#9670cb]">
            <a href={wa("Olá! Quero me inscrever no Círculo Sagrado da Reconexão Sagrada.")} target="_blank" rel="noreferrer">
              Quero participar
            </a>
          </Button>
        </div>

        <div className="grid gap-6 lg:grid-cols-[1.3fr_.7fr]">
          <Card className="rounded-[28px] border-white/60 bg-white/85 shadow-[0_18px_50px_rgba(88,58,122,0.10)]">
            <CardHeader>
              <CardTitle className="text-2xl text-[#5f476f]">
                Tema: {BRAND.circle.theme}
              </CardTitle>
              <CardDescription className="text-base text-slate-600">
                Uma noite para fortalecer a confiança, a presença e o seu poder de expansão.
              </CardDescription>
            </CardHeader>
            <CardContent className="grid gap-4 sm:grid-cols-2">
              {[
                [CalendarDays, "Data", BRAND.circle.date],
                [Clock3, "Horário", BRAND.circle.time],
                [MapPin, "Local", BRAND.circle.location],
                [Heart, "Valor", BRAND.circle.price],
              ].map(([Icon, label, value]) => {
                const Cmp = Icon as typeof CalendarDays;
                return (
                  <div key={label as string} className="rounded-2xl border border-[#efe2f4] bg-[#fffafc] p-4">
                    <div className="flex items-center gap-2 text-sm font-medium text-[#a07ab8]">
                      <Cmp className="h-4 w-4" /> {label as string}
                    </div>
                    <div className="mt-2 text-sm leading-relaxed text-slate-700">{value as string}</div>
                  </div>
                );
              })}
            </CardContent>
          </Card>

          <Card className="rounded-[28px] border-white/60 bg-white/85 shadow-[0_18px_50px_rgba(88,58,122,0.10)]">
            <CardHeader>
              <CardTitle className="text-xl text-[#5f476f]">Inscrição</CardTitle>
              <CardDescription className="text-slate-600">
                Reserve sua vaga e acompanhe novidades pelo Instagram.
              </CardDescription>
            </CardHeader>
            <CardContent className="space-y-3">
              <Button asChild className="w-full rounded-full bg-[#a988d8] text-white hover:bg-[#9670cb]">
                <a href={wa("Olá! Quero me inscrever no Círculo Sagrado (Poder em Expansão)." )} target="_blank" rel="noreferrer">
                  Participar pelo WhatsApp
                </a>
              </Button>
              <Button asChild variant="outline" className="w-full rounded-full border-[#d8c0f3] text-[#7a5aa8]">
                <a href={BRAND.instagram} target="_blank" rel="noreferrer">
                  <Instagram className="mr-2 h-4 w-4" /> Ver Instagram
                </a>
              </Button>
            </CardContent>
          </Card>
        </div>
      </section>

      <section id="catalogo" className="mx-auto max-w-6xl px-4 pb-16">
        <div className="mb-8 flex flex-col gap-4 md:flex-row md:items-end md:justify-between">
          <div>
            <div className="mb-3 inline-flex rounded-full bg-white/70 px-4 py-2 text-sm font-medium text-[#7a5aa8] shadow-sm">
              <ShoppingBag className="mr-2 h-4 w-4" /> Catálogo da marca
            </div>
            <h2 className="text-3xl font-semibold tracking-tight text-[#5f476f]">
              Produtos com alma, intenção e beleza
            </h2>
            <p className="mt-2 max-w-2xl text-sm leading-relaxed text-slate-600 sm:text-base">
              Uma vitrine delicada para apresentar suas criações, encomendas e peças especiais da Reconexão Sagrada.
            </p>
          </div>
          <EncomendaDialog />
        </div>

        <div className="grid gap-6 md:grid-cols-2 xl:grid-cols-3">
          {products.map((p, i) => (
            <ProductCard key={p.name} p={p} index={i} />
          ))}
        </div>
      </section>

      <section className="mx-auto max-w-6xl px-4 pb-16">
        <div className="mb-8 flex flex-col gap-4 md:flex-row md:items-end md:justify-between">
          <div>
            <div className="mb-3 inline-flex rounded-full bg-white/70 px-4 py-2 text-sm font-medium text-[#7a5aa8] shadow-sm">
              <Sparkles className="mr-2 h-4 w-4" /> Rituais & Energias
            </div>
            <h2 className="text-3xl font-semibold tracking-tight text-[#5f476f]">
              Intenções que podem guiar suas criações
            </h2>
            <p className="mt-2 max-w-2xl text-sm leading-relaxed text-slate-600 sm:text-base">
              Uma seção para apresentar o significado energético dos seus produtos e inspirar escolhas mais conectadas com cada momento.
            </p>
          </div>
        </div>

        <div className="grid gap-6 md:grid-cols-2 xl:grid-cols-4">
          {[
            {
              title: "Proteção",
              text: "Para momentos de fortalecimento, segurança energética e cuidado do campo espiritual.",
            },
            {
              title: "Prosperidade",
              text: "Intenção para abrir caminhos, estimular abundância e apoiar novos começos.",
            },
            {
              title: "Amor-próprio",
              text: "Para nutrir autoestima, acolhimento, presença e reconexão com a própria essência.",
            },
            {
              title: "Calma & limpeza",
              text: "Ideal para pausar, relaxar, descarregar tensões e restaurar a leveza interior.",
            },
          ].map((item) => (
            <Card key={item.title} className="rounded-[28px] border-white/60 bg-white/85 shadow-[0_18px_50px_rgba(88,58,122,0.08)]">
              <CardHeader>
                <CardTitle className="text-lg text-[#5f476f]">{item.title}</CardTitle>
              </CardHeader>
              <CardContent className="text-sm leading-relaxed text-slate-600">
                {item.text}
              </CardContent>
            </Card>
          ))}
        </div>
      </section>

      <section className="mx-auto max-w-6xl px-4 pb-16">
        <div className="grid gap-6 md:grid-cols-3">
          <Card className="rounded-[28px] border-white/60 bg-white/85 shadow-[0_18px_50px_rgba(88,58,122,0.08)]">
            <CardHeader>
              <CardTitle className="text-lg text-[#5f476f]">Como comprar</CardTitle>
            </CardHeader>
            <CardContent className="text-sm leading-relaxed text-slate-600">
              Escolha o produto ou a proposta desejada e clique no botão de atendimento para falar direto pelo WhatsApp.
            </CardContent>
          </Card>

          <Card className="rounded-[28px] border-white/60 bg-white/85 shadow-[0_18px_50px_rgba(88,58,122,0.08)]">
            <CardHeader>
              <CardTitle className="text-lg text-[#5f476f]">Personalizações</CardTitle>
            </CardHeader>
            <CardContent className="text-sm leading-relaxed text-slate-600">
              Capas, miolos, frases, detalhes, intenções, estampas e combinações podem ser pensadas de forma única para cada encomenda.
            </CardContent>
          </Card>

          <Card className="rounded-[28px] border-white/60 bg-white/85 shadow-[0_18px_50px_rgba(88,58,122,0.08)]">
            <CardHeader>
              <CardTitle className="text-lg text-[#5f476f]">Contato</CardTitle>
            </CardHeader>
            <CardContent className="space-y-3 text-sm text-slate-600">
              <Button asChild className="w-full rounded-full bg-[#a988d8] text-white hover:bg-[#9670cb]">
                <a href={wa("Olá! Quero tirar uma dúvida sobre a Reconexão Sagrada.")} target="_blank" rel="noreferrer">
                  <Phone className="mr-2 h-4 w-4" /> WhatsApp
                </a>
              </Button>
              <Button asChild variant="outline" className="w-full rounded-full border-[#d8c0f3] text-[#7a5aa8]">
                <a href={BRAND.instagram} target="_blank" rel="noreferrer">
                  <Instagram className="mr-2 h-4 w-4" /> Instagram
                </a>
              </Button>
              <div className="pt-1 text-xs text-slate-500">
                {BRAND.instagramHandle} • {BRAND.city}
              </div>
            </CardContent>
          </Card>
        </div>
      </section>
    </div>
  );
}
