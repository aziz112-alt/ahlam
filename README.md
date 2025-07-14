import { Button } from "@/components/ui/button";
import { Card, CardContent } from "@/components/ui/card";
import { Input } from "@/components/ui/input";
import { motion } from "framer-motion";
import { useState } from "react";

export default function HomePage() {
  const [image, setImage] = useState(null);

  const handleImageUpload = (e) => {
    const file = e.target.files[0];
    if (file) {
      setImage(URL.createObjectURL(file));
    }
  };

  return (
    <div className="min-h-screen bg-gradient-to-br from-black via-gray-900 to-black text-white p-6">
      <motion.h1
        className="text-5xl font-bold text-center mb-6"
        initial={{ opacity: 0, y: -30 }}
        animate={{ opacity: 1, y: 0 }}
        transition={{ duration: 0.8 }}
      >
        حول صورتك إلى فيديو ناطق بالذكاء الاصطناعي
      </motion.h1>

      <motion.p
        className="text-center text-lg max-w-2xl mx-auto mb-10 text-gray-300"
        initial={{ opacity: 0 }}
        animate={{ opacity: 1 }}
        transition={{ delay: 0.5, duration: 0.8 }}
      >
        ارفع صورة لك، أضف نصًا أو صوتًا، ودع تقنيتنا تحوّلها إلى فيديو تفاعلي ينبض بالحياة.
      </motion.p>

      <div className="grid grid-cols-1 md:grid-cols-2 gap-6 max-w-5xl mx-auto">
        <Card className="bg-white/5 border border-white/10 backdrop-blur-xl">
          <CardContent className="p-6">
            <h2 className="text-2xl font-semibold mb-4">جرّب الآن</h2>
            <Input type="file" accept="image/*" onChange={handleImageUpload} />
            {image && (
              <img
                src={image}
                alt="Uploaded"
                className="mt-4 rounded-xl shadow-xl border border-white/10"
              />
            )}
            <Button className="mt-4 w-full">تابع التحريك</Button>
          </CardContent>
        </Card>

        <Card className="bg-white/5 border border-white/10 backdrop-blur-xl">
          <CardContent className="p-6 flex flex-col justify-center h-full">
            <video
              src="/demo.mp4"
              controls
              className="rounded-xl shadow-xl border border-white/10"
            />
            <p className="text-sm text-gray-400 mt-2 text-center">
              مثال على فيديو تم توليده عبر موقعنا
            </p>
          </CardContent>
        </Card>
      </div>
    </div>
  );
}
